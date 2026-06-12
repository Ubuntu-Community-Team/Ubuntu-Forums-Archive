---
title: "HELP!, setup nvidia IR remote control with LIRC"
date: 2010-08-24
forum: Multimedia Software
---

### Post by LarsUb on 2010-08-24
Hi
I'm trying to set my custom remote control, and i'm not sure if this is just happening to me, since i haven found something similar in google, the issue is with  **irrecord** rev5.95

i'm previously stopped the lircd daemon and read the "adding new remote controls", as indicated in the LIRC website [http://www.lirc.org/html/configure.html](http://www.lirc.org/html/configure.html)
I installed LIRC, and bla bla.. im trying to set my custom remote control since it doesn't appear in the pre-detected list of devices, im using a Nvidia UR88A Remote with CM21A X10 RF Receiver (USB), both are part of the old FX5200 personal cinema.

Then, when i run  $ irrecord -d /dev/lirc0 ~\lirc
it passes the gap detection, but just that,
when i type the name for the buttons and press Enter.. **nothing more happens**, i expect the program would ask me to press the button in order to catch the IR signal, but this is not happening, i've waited 15 mins and pressed ENTER 50 time, so finally i have to press  Ctrl+C to escape.

I think this could be an error or bug, but not sure.
This is an issues's output:[INDENT]$ irrecord -d /dev/lirc0 ~\lirc
*bla bla bla*
Hold down an arbitrary button.
................................................................................
Found gap length: 135963
Now enter the names for the buttons.

Please enter the name for the next button (press <ENTER> to finish recording)
key_mute

        *here i wait 5 mins and pressed 20 times the ENTER key.*
^C
raul@ubuntu:~$
raul@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
raul@ubuntu:~$ 
raul@ubuntu:~$ lircd --version
lircd 0.8.6
raul@ubuntu:~$ 
raul@ubuntu:~$ irrecord --version
irrecord $Revision: 5.95 $
raul@ubuntu:~$ 
[/INDENT]I hope you guys can point me to some direction for solving this issue. 
Regards!

---

