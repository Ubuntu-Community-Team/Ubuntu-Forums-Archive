---
title: "Aodv"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by newuser10 on 2011-09-01
Hi.
I am an engineering student working on a networking project.i have to learn dynamic routing in ubuntu , installed aodv.uu for that. The packages aodv-uu and aodv-uu-source now appear in my synaptic pakage manager. But when i try running the application in terminal it gives me an error.
What i write in ubuntu: aodvd -l -r -3
(as a root)]
Error:
module kodv does not exist in /proc/modules

Can anyonu guide me through this please? I am totally new to ubuntu and don't know much.Thanks

---

### Post by northd_tech on 2011-09-01
Well first thing- you likely aren't running as "root" under Ubuntu.  You will probably need to put "**sudo**" in front of many/most commands when you are trying to get that AODV-uu module built (and you might even need "sudo su" occasionally).  Here is the documentation about sudo and "root":

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

What does Synaptic PM tell you about the version of AODV-uu that you have installed?  Is it newer or older than version 0.9.6 found here (from about April 13, 2011)?:

[http://sourceforge.net/projects/aodvuu/](http://sourceforge.net/projects/aodvuu/)

I'm hoping that newer sourcecode would compile easier.  Also, did you save any error messages from the Synaptic PM terminal window?  Posting those errors and warnings here might help if you get a bunch of errors (probably about missing header files).

It wouldn't hurt to run the 3 terminal commands found at post #2 on this very old thread:

**Installing AODV.uu**
[http://ubuntuforums.org/showthread.php?t=795000](http://ubuntuforums.org/showthread.php?t=795000)

EDIT:  I can't even get my Synaptic PM to display aodv-uu.  Did you add a repository to get access to that and which one?

---

### Post by newuser10 on 2011-09-02
[FONT=Calibri]
1. I am doing everything as root i am becoming root using sudo -s command.[/FONT]
   
   [FONT=Calibri]2.it gives me version 0.9.5-1[/FONT]
   
   [FONT=Calibri]3.Synaptic PM didnt give me any errors[/FONT]
   [FONT=Calibri]4.Iv already tried those commands.The first tells me that packages are already installed.[/FONT]
   The second one  works fine too and installs source and the third one again tells me that  all headers and packages are up to date. aodvd -l -r -3 still gives me  the same error
 5.I even tried:cd ~/src
 apt-get source linux-restricted-modules-common
 This gives me an error:unable to find source pkg for l-r-m common.
 6.i used module-assistant auto-install aodv-uu and then the packages appeared in Synaptic PM
 
  Please guide me.
 [FONT=Calibri]Thanks[/FONT]

---

### Post by newuser10 on 2011-09-02
also,when i give the command "make" it gives me [kodv] error 2

---

