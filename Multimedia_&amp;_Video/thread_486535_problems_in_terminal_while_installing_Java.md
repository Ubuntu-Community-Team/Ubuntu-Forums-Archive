---
title: "problems in terminal while installing Java"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by Nyxess on 2007-06-28
[B][I][B][I]this is my second day using ubuntu, so stick with me

i downloaded Frostwire and found out i needed java as well. so i followed the link in the system requirements for frostwear to [http://www.java.com/en/download/index.jsp](http://www.java.com/en/download/index.jsp) and continues to "Free Java Download" at which point i was to choose my operating system.

there were four choices for Linux:

Linux RPM (self-extracting file) filesize: 17.67 MB
Linux (self-extracting file) filesize: 18.15 MB
Linux x64 * filesize: 17.15 MB
Linux x64 RPM * filesize: 16.75 MB

i dont know how to tell which one i have, so i guessed the first. Now a file was downloaded onto my desktop(jre-1_5_0-linux-i586-rpm.bin)

next, i hit the "Instructions" link and followed these instructions:

1. At the terminal: Type:
su
2. Enter the root password.
3. Change to the directory in which you want to install. Type:
cd
For example, to install the software in the /usr/java/ directory, Type:
cd /usr/java

Note about root access: To install the JRE in a system-wide location such as/usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions.
4. Change the permission of the file you downloaded to be executable. Type:
chmod a+x jre-1_5_0-linux-i586-rpm.bin
5. Start the installation process. Type:
./jre-1_5_0-linux-i586-rpm.bin

This displays a binary license agreement. Read through the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation.



type YES to agree to the license agreement

6. The installation file creates jre-1_5_0-linux-i586.rpm file in the current directory.



RPM unpacking completes

7. Run the RPM command at the terminal to install the packages. Type:
rpm -iv jre-1_5_0-linux-i586.rpm
8. The JRE is installed in jre1.5.(version number) sub-directory under the current directory. In this case, the JRE is installed in the /usr/java/jre1.5.0 directory. Verify that the jre1.5.0 sub-directory is listed under the current directory. Type:
ls



Verify the installation filename

on the third step i typed "cd /usr/java" in the Terminal, and it spit out this

bash: cd: /usr/java: No such file or directory

so i just used "cd /usr/"

then in step four i followed the directions and it gave me this responce

chmod: cannot access `jre-1_5_0-linux-i586-rpm.bin': No such file or directory


im completly lost. plz help *L*[/I][/B][/I][/B]

---

