---
title: "Nova HD S2 IR Remote Issue"
date: 2009-01-02
forum: Multimedia Software
---

### Post by Propantriol on 2009-01-02
Hi,

yesterday I have installed Intrepid Ibex and almost everything but the IR Remote of my Nova HD S2 is working fine.

I just copied /etc/lirc/ from my Hardy installation which is supposed to work. Of course I have also edited the lircd.conf like it is described [here]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000#Remote_Control_Support").
I have also copied my .lircrc and after restarting lircd I executed 'irexec -d' but the remote is not working. It is more acting like a keyboard. So I can use the up, down, right, left buttons on my remote like the arrow keys on my keyboard. But buttons like pause or play don't work i.e. in vlc even though they worked in Hardy.

Any ideas on this?

Thanks in advance.

---

### Post by doug1212 on 2009-01-02
Hi,
No help I'm afraid, but you are not alone struggling with LIRC, there is a lot of correspondence at present between the kernel devs and the LIRC people, it seems partial functionality for certain remotes has been built into the kernel and is making full LIRC set up for the end user fraught.

Doug.

---

### Post by Propantriol on 2009-01-02
Hi, 

thanks for your reply. 
So you think their is very likely no solution for this issue?

Argh watching TV without remote really sucks :(

Nethertheless I don't give up hope of a solution ;-)

---

