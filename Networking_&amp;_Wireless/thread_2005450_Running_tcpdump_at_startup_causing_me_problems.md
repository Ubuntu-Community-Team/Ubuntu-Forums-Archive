---
title: "Running tcpdump at startup causing me problems"
date: 2012-06-17
forum: Networking &amp; Wireless
---

### Post by SparTacux on 2012-06-17
I recently created a script file to run tcpdump at startup. The file was placed in /etc/network/if-up.d

#!/bin/bash

tcpdump -s0 -i eth0 -C 50 -w /path/to/ capture-$(date +%a-%d%m%y-%H%M-%S).pcap

This works but has a few unwanted side effects. It sometimes creates two instances of the capture file and writes to both of them. The second problem is that my script file causes some of the other script files in if-up.d to stop working. I noticed my system wasn't making any NTP calls when the network first comes up. 

Another worry is that I'm running tcpdump as root user & could this compromise my system.?

I'm guessing writing a script file to do this isn't as simple as what I did and may need checks for multiple instances. I can't quite work out why it stops the NTP system from working only that there is a file for doing NTP in if-up.d and my file is affecting the working of this ntp script file.

---

### Post by matt_symes on 2012-06-17
Hi

> **SparTacux said:**
> I recently created a script file to run tcpdump at startup. The file was placed in /etc/network/if-up.d

#!/bin/bash

tcpdump -s0 -i eth0 -C 50 -w /path/to/ capture-$(date +%a-%d%m%y-%H%M-%S).pcap

This works but has a few unwanted side effects. It sometimes creates two instances of the capture file and writes to both of them.

Do you have multiple interfaces such as wireless as well as wired ?

You script will get called each time any interface goes up . You need to test that the interface going up is eth0.

> 
The second problem is that my script file causes some of the other script files in if-up.d to stop working. I noticed my system wasn't making any NTP calls when the network first comes up. 

You could try running it after the other scripts. Maybe that's the problem.

> Another worry is that I'm running tcpdump as root user & could this compromise my system.?

I'm not so sure of this. I would certainly feel far more comfortable running it as a non root user and that is what i would research how to do.

This is for openSUSE but i'm sure it could be modified :)

[http://peternixon.net/news/2012/01/28/configure-tcpdump-work-non-root-user-opensuse-using-file-system-capabilities/](http://peternixon.net/news/2012/01/28/configure-tcpdump-work-non-root-user-opensuse-using-file-system-capabilities/)

Let's see what others think.

Kind regards

---

### Post by SparTacux on 2012-06-18
Do you have multiple interfaces such as wireless as well as wired ?

Nope. I'm new to scripts and it looks like I need to read a book on the  subject. Looking at the other scripts in if-up.d there are checks for  different run levels and LOCK variables in use to stop multiple  instances of the same program being run. 
**************************************

You script will get called each time any interface goes up . You need to test that the interface going up is eth0.
You could try running it after the other scripts. Maybe that's the problem.

I'm guessing my script calls tcpdump and tcpdump doesn't exit because  it's continually in use capturing packets.  Therefore - it's possible  the script file never exits either which would stop further scripts in  if-up.d from running. 
*****************************************

I'm not so sure of this. I would certainly feel far more comfortable  running it as a non root user and that is what i would research how to  do.
This is for openSUSE but i'm sure it could be modified :smile:

[http://peternixon.net/news/2012/01/28/configure-tcpdump-work-non-root-user-opensuse-using-file-system-capabilities/](http://peternixon.net/news/2012/01/28/configure-tcpdump-work-non-root-user-opensuse-using-file-system-capabilities/)

Thanks for that. I saw something similar in Ubuntu to run wireshark as none root user. It looks like that is the way to go.

---

### Post by matt_symes on 2012-06-18
Hi

> **SparTacux said:**
> Nope. I'm new to scripts and it looks like I need to read a book on the  subject. Looking at the other scripts in if-up.d there are checks for  different run levels and LOCK variables in use to stop multiple  instances of the same program being run. 

Lock files are a standard way to ensure only one instance of a script runs at a time. I would store the pid of tcpdump when you create it so you can stop it when needs be.

> I'm guessing my script calls tcpdump and tcpdump doesn't exit because  it's continually in use capturing packets.  Therefore - it's possible  the script file never exits either which would stop further scripts in  if-up.d from running.

This sounds like a reasonable assumption given that you are only using one interface. You can check which interface rthe script is being called for using the "$IFACE" env variable.

You can add a script in /etc/network/if-down.d when the interface goes down to stop the dump as well (hence knowing the PID of tcpdump above)

> Thanks for that. I saw something similar in Ubuntu to run wireshark as none root user. It looks like that is the way to go.

If you need any help with this then just say the word :)

BTW: The > QUOTE button is on the toolbar above where you type and looks like a square speech bubble. 

Use it when quoting people from previous posts. It make each post much easier to read.

Kind regards

---

### Post by SparTacux on 2012-06-29
> **matt_symes said:**
> 

If you need any help with this then just say the word :)


Kind regards

Thanks matt

Any chance you can loan me £3 million pounds too :-)

---

### Post by matt_symes on 2012-06-29
Hi

> **SparTacux said:**
> Thanks matt

Any chance you can loan me £3 million pounds too :-)

LOL. Can i write you a cheque ? :D

Kind regards

---

### Post by SparTacux on 2012-06-29
> **matt_symes said:**
> Hi

LOL. Can i write you a cheque ? :D

Kind regards

That will do nicely ;-)

The weird thing about those extra instances of capture files is that on one occasion it was capturing what appeared to be USB data packets. I missed out the -i eth0 argument on tcpdump but I was under the impression that tcpdump defaults to eth0 anyway. 

What happened to the good old days of config.sys and autoexec.bat - it was really simple then. :-)

If you feel up to it ( and can find the time ) I wouldn't mind seeing what you would do to run tcpdump from a script file in if-up.d. I could call the script file zcapture so that it would run last ( presuming they  run in alphabetical order ) and that would allow the other scripts in if-up.d to run first. I'm not sure if there is a way of calling tcpdump from within the script without the script waiting for tcpdump to exit before continuing. Maybe?

I never thought of stopping tcpdump on a network down script.

Cheers

---

### Post by matt_symes on 2012-07-02
Hi

> If you feel up to it ( and can find the time ) I wouldn't mind seeing  what you would do to run tcpdump from a script file in if-up.d. I could  call the script file zcapture so that it would run last ( presuming they   run in alphabetical order ) and that would allow the other scripts in  if-up.d to run first. I'm not sure if there is a way of calling tcpdump  from within the script without the script waiting for tcpdump to exit  before continuing. Maybe?

I will have a go at thhis as soon as i find some time. 

It's something i am interesting in myself. I have started it but have not finished it yet.

I will post the scripts in the next couple of days but i am extremely busy at the moment.

Kind regards

---

