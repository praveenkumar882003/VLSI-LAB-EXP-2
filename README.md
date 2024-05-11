# SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

**AIM:** 
 To simulate and synthesis Logic Gates,Adders and Subtractor using Vivado Software
 
**APPARATUS REQUIRED :**  Vivado™ ML 2023.2

**PROCEDURE :**
1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

**LOGIC DIAGRAM**

ENCODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)


DECODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)


MULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)


DEMULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/1c45a7fc-08ac-4f76-87f2-c084e7150557)


MAGNITUDE COMPARATOR

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2)


  


**EXPERIMENTS :**

#1
DECODER_3TO8:-

Code:
~~~
module decoder_struct(  
  input [2:0] a,    
  output [7:0] d    
   );
wire x,y,z;
not g1(z,a[0]);
not g2(y,a[1]);
not g3(x,a[2]);
and g4(d[0],x,y,z);
and g5(d[1],x,y,a[0]);
and g6(d[2],x,a[1],z);
and g7(d[3],x,a[1],a[0]);
and g8(d[4],a[2],y,z);
and g9(d[5],a[2],y,a[0]);
and g10(d[6],a[2],a[1],z);
and g11(d[7],a[2],a[1],a[0]);
endmodule
~~~



OUTPUT:-

Simulation:

![image](https://github.com/lycanthrope004/VLSI-LAB-EXP-2/assets/121667830/55e67f15-028f-47ab-81f1-64eb42a874ad)

Elaborated Design:

![image](https://github.com/lycanthrope004/VLSI-LAB-EXP-2/assets/121667830/a6ab2587-f080-4337-8744-a3ce5a48083d)

#2
DEMULTIPLEXER_1TO8:-

Code:
~~~
module demux_1_8(y,s,a);
output reg [7:0]y;
input [2:0]s;
input a;

always @(*)
begin 
y=0;
case(s)
3'd0: y[0]=a;
3'd1: y[1]=a;
3'd2: y[2]=a;
3'd3: y[3]=a;
3'd4: y[4]=a;
3'd5: y[5]=a;
3'd6: y[6]=a;
3'd7: y[7]=a;
endcase
end
endmodule
~~~

OUTPUT:-

Simulation:

![image](https://github.com/lycanthrope004/VLSI-LAB-EXP-2/assets/121667830/6f259c21-c152-489b-8f03-b319a667cc74)

Elaborated Design:

![image](https://github.com/lycanthrope004/VLSI-LAB-EXP-2/assets/121667830/5e679288-7f30-4cc1-89ab-cf8f9100d6ef)

#3
ENCODER_8to3:-

Code:
~~~
module encoder_8_to_3(a0,a1,a2,d0,d1,d2,d3,d4,d5,d6,d7);
input d0,d1,d2,d3,d4,d5,d6,d7;
output a0,a1,a2;
or g1(a0,d1,d3,d5,d7);
or g2(a1,d2,d3,d6,d7);
or g3(a2,d4,d5,d6,d7);
endmodule

~~~

OUTPUT:-

Simulation:

![image](https://github.com/lycanthrope004/VLSI-LAB-EXP-2/assets/121667830/568bd01a-8eea-45a2-b033-4b433f67f883)

Elaborated Design:

![image](https://github.com/lycanthrope004/VLSI-LAB-EXP-2/assets/121667830/b3745ffe-493a-44c5-9f74-8a99f2c32b28)

#4
MAGNITUDE_COMPARATOR:-

Code:
~~~
module comparator(a,b,eq,lt,gt);
input [3:0] a,b;
output reg eq,lt,gt;
always @(a,b)
begin
 if (a==b)
 begin
  eq = 1'b1;
  lt = 1'b0;
  gt = 1'b0;
 end
 else if (a>b)
begin
  eq = 1'b0;
  lt = 1'b0;
  gt = 1'b1;
 end
 else
 begin
  eq = 1'b0;
  lt = 1'b1;
  gt = 1'b0;
 end
end 
endmodule
~~~

OUTPUT:-

Simulation:

![image](https://github.com/lycanthrope004/VLSI-LAB-EXP-2/assets/121667830/8c173599-802a-4297-ad2d-ab1c5b537f77)

Elaborated Design:

![image](https://github.com/lycanthrope004/VLSI-LAB-EXP-2/assets/121667830/3ed0152f-6e86-4c81-adb5-3deb95aa9451)

#5
MULTIPLEXER_8TO1:-

Code:
~~~
module mux_8tol (in, sel, out);
    input [7:0] in;
    input [2:0] sel;
    output reg out;
    always @(*)
       begin
          case (sel)
              3'b000: out = in [0];
              3'b001: out = in [1];
              3'b010: out = in [2];
              3'b011: out = in [3];
              3'b100: out = in [4];
              3'b101: out = in [5];
              3'b110: out = in [6];
              3'b111: out = in [7];
              default: out = 1'bx;
          endcase
       end
endmodule
~~~
OUTPUT:-

Simulation:
![image](https://github.com/lycanthrope004/VLSI-LAB-EXP-2/assets/121667830/d8d9bddb-adde-45cb-8046-d12d8886f7a0)



Elaborated Design:
![image](https://github.com/lycanthrope004/VLSI-LAB-EXP-2/assets/121667830/e76f843c-3d83-4e20-8ea7-b887494303d2)


**RESULT :**  The Simulation and Synthesis Logic Gates,Adders and Subtractor is successfully verified using Vivado Software .

