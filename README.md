Download Link: https://assignmentchef.com/product/solved-cs3750-homework7-program-to-implement-a-simplified-nist-rbac-model
<br>
<strong>Part II: Task I . Write a Java program to implement a simplified NIST RBAC model. </strong>(The topology and examples here

<table width="720">

 <tbody>

  <tr>

   <td width="645">are provided for you to test your program.  The instructor will use similar but different test cases to test your program.</td>

   <td width="75">Your program</td>

  </tr>

  <tr>

   <td width="645">will be evaluated according to how much it can accomplish and the test cases that it can pass INSTEAD OF code review.</td>

   <td width="75">) <strong> </strong></td>

  </tr>

 </tbody>

</table>

<ol>

 <li><strong>Data structures:</strong> it is up to you to choose <strong>appropriate data structures</strong> to maintain <em>role hierarchy</em>, <em>user-role matrix</em>, <em>role-object matrix</em>, etc.</li>

 <li><strong>Role Hierarchy</strong>: this program must support role hierarchy defined in NIST RBAC.

  <ul>

   <li>This program reads a role hierarchy from file “<em>txt</em>”. Each line in this file is formatted as “&lt;ascendant&gt;   &lt;descendant&gt;”. For example, for the role hierarchy on the right, the first several lines in roleHiearchy.txt is</li>

  </ul></li>

</ol>

<strong>R8            R6 </strong>

<strong> R9             R7 </strong>

<strong> R10            R7 </strong>

<strong> …… </strong>

<ul>

 <li>The contents of this text file must be <strong>validated</strong> to enforce the “limited role hierarchies” defined in NIST RBAC (See the slide titled “<strong>Hierarchical RBAC</strong>”). For an <strong>invalid</strong> file, (1) <strong>close</strong> the file, (2) <strong>display</strong> “invalid line is found in roleHierarchy.txt: line &lt;line # of the first invalid line&gt;, enter any key to read it again” to allow user to fix the problem, (3) once reading any user input, go back to <strong>2</strong>. <strong>Continue</strong> if it’s <strong>valid</strong>.</li>

 <li><strong>Display</strong> the role hierarchy <strong>top down</strong>. If you may display it as a tree, it is great.  Otherwise, the following format is fine.</li>

</ul>

<strong>R1—&gt;R2, R3 </strong>

<strong> R2—&gt;R4, R5, R6 R3—&gt;R7 </strong>

<strong> …… </strong>

<ol start="3">

 <li><strong>Objects: </strong>This program reads all <strong><em>resource objects</em></strong> from file “<em>txt</em>”, which contains ONE line. For example,</li>

</ol>

<strong>                </strong><strong>F1     F2     F3     F4     P1     P2     P3     D1     D2 </strong>

<ul>

 <li>Validate objects for duplication. For an <strong>invalid</strong> file, (1) <strong>close</strong> the file, (2) <strong>display</strong> “duplicate object is found: &lt; object&gt;, enter any key to read it again” to allow user to fix the problem, (3) once reading any user input, go back to <strong>1</strong>. <strong>Continue</strong> if it’s <strong>valid</strong>.</li>

 <li>Display the current <em>role-object matrix</em> with null entries. If necessary, you may break this matrix into multiple sub-matrices for displaying by limiting up to 5 columns per sub-matrix. For example,</li>

</ul>

<strong>       R1     R2     R3     R4     R5      </strong>

<strong>R1  </strong>

<strong>…… </strong>

<strong>       R6     R7     R8     R9     R10 </strong>

<strong>R1  </strong>

<strong>…… </strong>

<strong>… … … … … … … </strong>

<ol start="4">

 <li><strong>Granting Permissions to Roles with Inheritance</strong>:</li>

</ol>

MSU Denver, M&amp;CS                                       CS 3750-001: Computer and Network Security, Fall 2019                                          Dr. Weiying Zhu

<ul>

 <li>This program must support role inheritance described as “the upper role includes all of the access rights of the lower role, as well as other access rights not available to the lower role” in the slide titled “<strong>Role Hierarchy</strong>”. In <strong>3</strong>, <strong>4.4</strong>, and <strong>4.5</strong>, whenever a permission is granted to a role, it must be <strong>inherited</strong> by <strong>all</strong> the <strong>descendants</strong> of this role.</li>

 <li><strong>Redundancy</strong> must be avoided. For example, when adding “read” by R2 to F1, if “read” is already there, don’t add it again.</li>

 <li>Update the <em>role-object matrix</em> to grant “control” by EACH role to itself. (See <strong>1</strong>). E.g., R8, R6, R2, and R1 “control” R8.</li>

 <li>Update the <em>role-object matrix</em> to grant “own” by the descendent of EACH role to it. (See <strong>1</strong>). E.g., R6, R2, and R1 “own” R8.</li>

 <li>This program also reads permissions to roles from file “<em>txt</em>”. Each line in this file is formatted as “&lt;role&gt; &lt;access right&gt;      &lt;object&gt;”, where a permission is an access right to an object. For example, after reading the following two lines, R6, R2, and R1 have “write*” to F3, and R2 and R1 have “seek” to D1.</li>

</ul>

<strong>                </strong><strong>R6     write*       F3 </strong>

<strong>R2  seek           D1 </strong>

<ul>

 <li>Display the current <em>role-object matrix</em> in the same format as what is used in <strong>step 3.2</strong>.</li>

</ul>

<ol start="5">

 <li><strong>SSD: </strong>This program reads <strong><em>mutually exclusive</em></strong> (when <em>n</em> = 2) and <strong><em>cardinality constraints</em></strong> (when n&gt;= 3) from file “<em>txt</em>”.

  <ul>

   <li>Each line includes a constraint given by the value of <em>n</em> and a set of roles. For example,</li>

  </ul></li>

</ol>

<strong>                </strong><strong>3      R2     R4     R5     R6     R8 </strong>

<strong>2       R1  R2      R4 </strong>

<strong>…… </strong>

<strong>Note</strong>: <strong><em>n</em></strong> MUST be &gt;= 2 to be valid.  For an <strong>invalid</strong> case, (1) <strong>close</strong> the file, (2) <strong>display</strong> “invalid line is found in roleSetsSSD.txt: line &lt;line # of the first invalid line&gt;, enter any key to read it again” to allow user to fix the problem, (3) once reading any user input, go back to Step <strong>5</strong>. <strong>Continue</strong> if it’s <strong>valid.  </strong><strong> </strong>

<ul>

 <li>Display all the constraints, one in a line. For example,</li>

</ul>

<strong>Constraint 1, n = 3, set of roles = {R2, R4, R5, R6, R8} … </strong>

<ol start="6">

 <li>This program constructs the <em>user-role matrix</em> by reading file <em>txt</em>. Each line is formatted as “&lt;user&gt; &lt;list of roles&gt;”.

  <ul>

   <li>While reading each line and updating the <em>user-role matrix</em>, the <strong>SSD constraints</strong> configured in Step <strong>5</strong> <strong>must be enforced</strong>. It is <strong>also</strong> <strong>invalid</strong> if two or more lines contain the same user. For an <strong>invalid</strong> file, (1) <strong>close</strong> the file, (2) <strong>display</strong> “invalid line is found in usersRoles.txt: line &lt;line # of the first invalid line&gt; due to &lt;constraint #? or duplicated user&gt;, enter any key to read it again” to allow user to fix the problem, (3) once reading any user input, go back to Step <strong>6</strong>. <strong>Continue</strong> if it’s</li>

  </ul></li>

</ol>

<strong>                </strong><strong>U1     R2     R5 </strong>

<strong>…… </strong>

<ul>

 <li>Display the <em>user-role matrix</em>. For example,</li>

</ul>

<strong>       R1     R2     R3     R4     R5     R6     R7     R8     R9     R10 </strong>

<strong>U1            +                    + </strong>

<strong>…… </strong>

<ol start="7">

 <li><strong>Query</strong> for a given User, a given pair of User and Object, or a given combination of (User, Access Right, Object)

  <ul>

   <li>Display the following messages to get three user inputs: <strong>user</strong>, <strong>object</strong>, and <strong>accessRight</strong>.</li>

  </ul></li>

</ol>

<strong>Please enter the user in your query: </strong>

<strong>Please enter the object in your query (hit enter if it’s for any): </strong>

<strong>Please enter the access right in your query (hit enter if it’s for any): </strong>

<ul>

 <li>if <strong>user</strong> isn’t in the <em>user-role matrix</em>, display “invalid user, try again.” and go back to Step 7.1. Otherwise, <strong>continue</strong>.</li>

 <li>if <strong>object</strong> and <strong>accessRight</strong> are empty, <strong>display</strong> all the objects that this user has access rights to as “&lt;object&gt; &lt;list of access rights to this object&gt;”, and then <strong>go to</strong> Step 7.7.  Otherwise, <strong>continue</strong>.  To keep it simple, if a user has the same or different lists of access rights to the same object due to different roles assumed by this user, you don’t have to merge them. For example,</li>

</ul>

<strong>R4     control, own </strong>

<strong>F1     read, write, execute </strong>

<strong>       R4     own </strong>

<strong>… </strong>

<ul>

 <li>if <strong>object</strong> isn’t in the <em>user-role matrix</em>, display “invalid object, try again.” and go back to Step 7.1. Otherwise, continue.</li>

 <li>if <strong>accessRight</strong> is empty, <strong>display</strong> all the access rights this user has to this object and <strong>go to</strong> Step 7.7. Otherwise, continue.</li>

 <li>check whether this <strong>user</strong> has the given <strong>accessRight</strong> to this <strong>object</strong>. If yes, display “authorized”, otherwise, display “rejected”.</li>

 <li>Display “Would you like to continue for the next query?” If the user inputs “yes”, go back to Step 7.1. Otherwise, exit.</li>

</ul>




<strong>Task II (10%)</strong>:<strong> Test your program on cs3750a. </strong>

<ol>

 <li>MAKE a directory “<strong>HW07</strong>” under your home directory on <strong>msdenver.edu</strong>.</li>

 <li>UPLOAD, COMPILE, and TEST your program under “<strong>HW07</strong>” on <strong>msdenver.edu</strong>.</li>

 <li>SAVE <strong><em>ALL your .txt input files</em></strong> and a <strong><em>file named</em></strong> <strong><em>txt</em></strong> under “<strong>HW07</strong>” on cs3700a.msudenver.edu, which captures the outputs of your program when you test it. You can use the following commands to redirect the standard output (stdout) to a <strong>file</strong> on UNIX, Linux, or Mac, and view the contents of the file</li>

</ol>

<strong>java prog_name_args | tee testResults.txt //copy stdout to the .txt file cat file-name     //display the file’s contents. </strong>