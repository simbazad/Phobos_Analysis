# Phobos Analysis
Phobos Ransomware Analysis

# Password for phobos_sample.zip --> "infected"

# Update : 

Apparently this phobos variant searches for C:\k.txt to extract its TEA key so it can decrypt its full payload.

![img](pic/3.png?raw=true "img")

![img](pic/4.png?raw=true "img")
(closer look)

Take a look at the breakpoint in the above img, if the content of k.txt isn't right the CMP instruction will compare the 4 bytes in SS:[EBP-8] with the 4-byte integer constant 10.
this memory adress contains:

![img](pic/5.png?raw=true "img")

so on the JNZ instruction we will jump and get TerminateProcess, lets patch it and continue.


![img](pic/1.png?raw=true "img")


![img](pic/2.png?raw=true "img")


![img](pic/6.png?raw=true "img")

As you can see the malware scrumble the file before deleting it so recovering k.txt is probably impossible.

# https://www.virustotal.com/#/file/8b0ee66b23e6a3ea684254df40a8a443103324b5c6bec3f2872ea1441a2024da/detection

#If someone holds both the malware and the key please share it!

