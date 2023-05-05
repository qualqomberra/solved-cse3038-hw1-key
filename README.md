Download Link: https://assignmentchef.com/product/solved-cse3038-hw1-key
<br>



<ol>

 <li>For the following C statement, what is the corresponding MIPS assembly code? Assume that the variables f, g, h, i, and j are assigned to registers $s2, $s3, $s4, $s5, and $s6, respectively. Assume that the base address of the arrays A and B are in registers $s0 and $s1, respectively. B[i+3] = A[i+4*j];</li>

</ol>

<strong><u>Answer:</u>  </strong>

<table width="314">

 <tbody>

  <tr>

   <td width="144">sll $t0, $s6, 2</td>

   <td width="48"> </td>

   <td width="122"># $t0 = 4*j</td>

  </tr>

  <tr>

   <td width="144">add $t0, $s5, $t0</td>

   <td width="48"> </td>

   <td width="122"># $t0 = 4*j + i</td>

  </tr>

  <tr>

   <td width="144">sll $t0, $t0, 2</td>

   <td width="48"> </td>

   <td width="122"># $t0 = t0*4</td>

  </tr>

  <tr>

   <td width="144">add $t0, $t0, $s0</td>

   <td width="48"> </td>

   <td width="122"># $t0 = &amp;A[i+4*j]</td>

  </tr>

  <tr>

   <td width="144">lw $t1, 0($t0)</td>

   <td width="48"> </td>

   <td width="122"># $t1 = A[i+4*j]</td>

  </tr>

  <tr>

   <td width="144">addi $t2,$s5,3</td>

   <td width="48"> </td>

   <td width="122"># $t2 = i+3</td>

  </tr>

  <tr>

   <td width="144">sll $t2,$t2,2</td>

   <td width="48"> </td>

   <td width="122"># $t2 = t2*4</td>

  </tr>

  <tr>

   <td width="144">add $t2,$t2,$s1</td>

   <td width="48"> </td>

   <td width="122"># $t2 = &amp;B[i+3]</td>

  </tr>

  <tr>

   <td width="144">sw $t1, 0($t2)</td>

   <td width="48"> </td>

   <td width="122"># B[i+3] = $t1</td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<ol start="2">

 <li>Show how the value 0xcabd1f2e would be arranged in memory of a little-endian and a big-endian machine. Assume the data is stored starting at address 0.</li>

</ol>




<strong><u>Answer:</u>  </strong>

Little Endian

<table width="114">

 <tbody>

  <tr>

   <td width="67">Address</td>

   <td width="47">Data</td>

  </tr>

  <tr>

   <td width="67">0</td>

   <td width="47">2e</td>

  </tr>

  <tr>

   <td width="67">1</td>

   <td width="47">1f</td>

  </tr>

  <tr>

   <td width="67">2</td>

   <td width="47">bd</td>

  </tr>

  <tr>

   <td width="67">3</td>

   <td width="47">ca</td>

  </tr>

 </tbody>

</table>







Big Endian

<table width="114">

 <tbody>

  <tr>

   <td width="67">Address</td>

   <td width="47">Data</td>

  </tr>

  <tr>

   <td width="67">0</td>

   <td width="47">ca</td>

  </tr>

  <tr>

   <td width="67">1</td>

   <td width="47">bd</td>

  </tr>

  <tr>

   <td width="67">2</td>

   <td width="47">1f</td>

  </tr>

  <tr>

   <td width="67">3</td>

   <td width="47">2e</td>

  </tr>

 </tbody>

</table>







<ol start="3">

 <li>Translate the following C code to MIPS. Assume that the variables f, g, h, i, and j are assigned to registers $s0, $s1, $s2, $s3, and $s4, respectively. Assume that the base address of the arrays A and B are in registers $s6 and $s7, respectively. Assume that the elements of the arrays A and B are 4-byte words: B[i+j+1] = A[i+j-2] + A[i-j+1]; <strong><u>Answer:</u> </strong></li>

</ol>

sub $t0, $s3, $s4                     # $t0 = i – j add $t1, $s3, $s4                  # $t1 = i + j

addi $t0,$t0,1                          # $t0 = i – j+1

addi $t2,$t1,1                          # $t2 = i + j + 1

addi $t1,$t1,-2                         # $t1 = i + j-2

sll $t0, $t0, 2                            # $t0 = (i-j+1)*4

sll $t1, $t1, 2                            # $t1 = (i+j-2)*4

add $t3, $s6, $t0                       # $t3 = &amp;A[i-j+1]

add $t4, $s6, $t1                       # $t4 = &amp;A[i+j-2]

lw $t5, 0($t3)                           # $t5 = A[i-j+1]

lw $t6, 0($t4)                           # $t6 = A[i+j-2]

add $t7, $t5, $t6                      # $t7 = A[i+j-2] + A[i-j+1]

sll $t2,$t2,2                             # $t2 = (i+j+1)*4

add $t2,$t2,$s7                        # $t2 = &amp;B[i+j+1]

sw $t7, 0($t2)                          # B[i+j+1] = $t7

<strong> </strong>

<ol start="4">

 <li>Provide the type, assembly language instruction, and binary representation of instruction described by the following MIPS fields:</li>

</ol>

op=0, rs=5, rt=8, rd=20, shamt=0, funct=36.




<strong><u>Answer:</u>  </strong>

Its R type instruction

Op=0 funct=36 è and




and $20, $5, $8            or

and $s4, $a1, $t0




<ol start="5">

 <li>For the following C statement, write a minimal sequence of MIPS assembly instructions that does the identical operation. Assume $t1 = A, $t2 = B, and $s1 is the base address of C.</li>

</ol>

A = C[0] &lt;&lt; 8;

<strong><u>Answer:</u>  </strong>




lw $t3, 0($s1) sll $t1, $t3, 8




<ol start="6">

 <li>Translate the following C code to MIPS assembly code. Use a minimum number of instructions. Assume that the values of a, b, i, and j are in registers $s0, $s1, $t0, and $t1, respectively. Also, assume that register $s2 holds the base address of the array D.</li>

</ol>

for(i=0; i&lt;a; i++)  for(j=0; j&lt;b; j++)

D[2*i] = i + j-5; <strong><u>Answer:</u>  </strong>




addi $t0, $0, 0 beq $0, $0, TEST1 LOOP1: addi $t1, $0, 0 beq $0, $0, TEST2 LOOP2: add $t3, $t0, $t1

sub $t3,$t3,5 sll $t2, $t0, 3 add $t2, $t2, $s2 sw $t3, ($t2) addi $t1, $t1, 1 TEST2: slt $t2, $t1, $s1 bne $t2, $0, LOOP2 addi $t0, $t0, 1

TEST1: slt $t2, $t0, $s0 bne $t2, $0, LOOP1

<ol start="7">

 <li>How many MIPS instructions does it take to implement the C code from Exercise 2.27 ? If the variables a and b are initialized to 10 and 1 and all elements of D are initially 0, what is the total number of MIPS instructions that is executed to complete the loop?</li>

</ol>

<strong><u>Answer:</u>  </strong>

14 instructions to implement and 144 instructions executed

<table width="1051">

 <tbody>

  <tr>

   <td width="160"></td>

   <td width="28">1</td>

   <td width="28">2</td>

   <td width="28">3</td>

   <td width="28">4</td>

   <td width="28">5</td>

   <td width="28">6</td>

   <td width="28">7 </td>

   <td width="28">8</td>

   <td width="28">9</td>

   <td width="28">10</td>

   <td width="28">11</td>

   <td width="28">12</td>

   <td width="28">13</td>

   <td width="28">14</td>

   <td width="28">15</td>

   <td width="28">16</td>

   <td width="28">17</td>

   <td width="28">18</td>

   <td width="28">19</td>

   <td width="28">20</td>

   <td width="28">21</td>

   <td width="28">22</td>

   <td width="28">23</td>

   <td width="28">24</td>

   <td width="28">25</td>

   <td width="28">26</td>

   <td width="28">27</td>

   <td width="28">28</td>

   <td width="28">29</td>

   <td width="28">30</td>

   <td width="31">31</td>

   <td width="28">32</td>

  </tr>

  <tr>

   <td width="160">1 addi $t0, $0, 0</td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="31"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="160">2 beq $0, $0, TEST1</td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="31"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="160">3 LOOP1: addi $t1, $0, 0</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="31"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="160">4 beq $0, $0, TEST2</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="31"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="160">5 LOOP2: add $t3, $t0, $t1</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="31"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="160">6 sll $t2, $t1, 4</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="31"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="160">7 add $t2, $t2, $s2</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="31"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="160">8 sw $t3, ($t2)</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="31"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="160">9 addi $t1, $t1, 1</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="31"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="160">10 TEST2: slt $t2, $t1, $s1 </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="31"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="160">11 bne $t2, $0, LOOP2</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="31"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="160">12 addi $t0, $t0, 1</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="31"> </td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="160">13 TEST1: slt $t2, $t0, $s0</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="31">*</td>

   <td width="28"> </td>

  </tr>

  <tr>

   <td width="160">14 bne $t2, $0, LOOP1</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28">*</td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="28"> </td>

   <td width="31"> </td>

   <td width="28">*</td>

  </tr>

 </tbody>

</table>

Inner loop will execute ones since b is 1