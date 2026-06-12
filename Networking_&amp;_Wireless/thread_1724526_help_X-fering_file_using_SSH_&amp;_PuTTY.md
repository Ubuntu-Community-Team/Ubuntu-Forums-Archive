---
title: "help X-fering file using SSH &amp; PuTTY"
date: 2011-04-08
forum: Networking &amp; Wireless
---

### Post by ARhere on 2011-04-08
Hello Ubuntu people-who-are-smarter-than-me,

I am trying to transfer a file from my work Win7 computer, to my Ubuntu home server.  I can SSH into my server using PuTTY with no problems.  I am now trying to push a file using the command
```
pscp c:\documents\foo.txt andrew@server.com:/home/andrew
``` and I am typing this in the PuTTY "Host Name(or IP address)" window.
When I do this, this is what I get...

```
Using username "pscp C:\documents\foo.txt andrew".
pscp C:documents\foo.txt andrew@server.com's password:
Access denied
pscp C:documents\foo.txt andrew@server.com's password:
```
The "Access denied" occurs after I type my password of course.
I just want to push a file from my Win7 machine to my Ubuntu using SSH and PuTTY.  PuTTY is what I have loaded on my work machine.

-AR

---

### Post by Doug S on 2011-04-08
[FONT=Calibri][SIZE=3]Interesting. I tried exactly what you did (same syntax and all) on my system and it worked fine. However, my password request line looked different than yours, where it did not list the file name also. Below is my example cut and pasted from my dos-box (or command prompt or whatever windows calls it now).[/SIZE][/FONT]
```
 
C:\Users\Doug\SPlot\scripts>"c:\program files\putty\pscp" c:\users\doug\splot\scripts\eth1_001.spt doug@ns1.smythies.com:/home/doug
doug@ns1.smythies.com's password:
eth1_001.spt              | 9 kB |   9.5 kB/s | ETA: 00:00:00 | 100%

```
[FONT=Calibri][SIZE=3]Your post appears to show an issue parsing out the user name. It is not clear to me why that is happening.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Note: I did the above on a Vista computer, but I could try it later on a windows 7 box if we think that might be the difference.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[FONT=Calibri][SIZE=3]... Later... Windows 7 box also worked fine.[/SIZE][/FONT]

---

### Post by ARhere on 2011-04-08
Interesting.  It must be the fact that I am using the GUI must be screwing it up.  I am using the standalone GUI EXE to run PuTTY and then entering the command in the destination box.  It is not installed anywhere.

The "About" button simply says "PuTTY Release 0.60".

I was not aware that PuTTY also came in a DOS Prompt flavor.

---

### Post by Doug S on 2011-04-09
First, my use of the term "DOS Prompt" was incorrect. That term has not been used with windows type operating systems for many many years now. I should have referred to creating a non GUI command line terminal window on a windows computer as "Command Prompt:" You can create one in many ways. One way is to double click on the icon that is typically a black box with a C:\_ inside in white and the name "Command Prompt". The icon is normally under the accessories folder under the "all programs" menu under the start tab on the left of the windows tool bar. Sometimes, there is a shortcut on the desktop. Another way is to depress and hold the "windows" key on your keyboard and then depress the "R" key. This will open a Run dialog box. Type "cmd.exe" and click "OK". (I do not know the key sequence if your keyboard is old and does not have the "windows" logo key button.)
I am not saying that PuTTY comes in a command line, non-GUI, version. As far as I know, it only comes in the GUI version. I am using version 0.60 also. Included with the PuTTY program, and optionally installed during the PuTTY installation, is the command line only, non-GUI, program "pscp.exe". It is this program that you want to execute from within a windows 7 non GUI command line environment. The "pscp.exe" program is independent of the PuTTY program, and you do not need to have PuTTY running or connected. 
I am not certain, but from my understanding of your reply you were executing a "pscp" executable on your Ubuntu computer via your GUI PuTTY session. There is not normally a "pscp" executable on Ubuntu systems that I have used (I use only server systems). However your syntax failure is consistent with "scp". What is the output from the command "locate pscp" on your ubuntu computer? If there is no output listing from that command, then my interpretation of your reply is incorrect and you should consider ignoring this reply.
Notice that my command line included the entire path to the "pscp.exe" executable. That is because I never set the path environment variable to include the PuTTY group of programs. My posted example above was from a windows vista 32 bit computer. I do not know if your computer set the path to include the PuTTY directory, or if your PuTTY installation even included the pscp.exe program, or if your PuTTY directory was placed in the default location. On my windows 7 64 bit computer, without the path variable set, I had to enter (something like) the following:
> C:\Users\Doug>"c:\program files (x86)\putty\pscp" c:\users\doug\bla.txt [EMAIL="doug@ns1.smythies.com"]doug@ns1.smythies.com[/EMAIL]:/home/doug
If you are uncomfortable with the windows command line level environment, then I am sure some forum readers could recommend a windows GUI sftp client. I am not knowledgeable about sftp GUI clients.

---

