---
title: "Please Help me VDR no sound problem"
date: 2010-04-02
forum: Multimedia Software
---

### Post by doctor_ahmed on 2010-04-02
I'm New at Linux So please make your help at simple form

I installed Ubuntu 9.10
after long search and facing many problems Finaly I have succeded to install VDR  1.7.10  using Synaptic manager 

and make it work but the problem

when i start VDR using  this command
 /etc/init.d/vdr start
I must run xhost + before it to display picture
but There is no sound at all

my xinliboutput configutation is
--local=sxfe
--primary
--video=xv
--fullscreen
--width=800
--height=600
--audio=alsa
--remote=127.0.0.1:37890


BUT !!  when i start using  command
vdr -P"xineliboutput"

I works well displaying image and sound without problems !!!!

WHERE IS MY PROBLEM?

I can run it using Second Command  but it needs to add all plugins manually  like this 
vdr -Pchannellists -Pfemon -Pxineliboutput

and it alway wait for remote response  

What is best method to start VDR with my plugins without problems

Please Help me   I have tired from long search

---

### Post by doctor_ahmed on 2010-04-02
still wating for help

---

### Post by doctor_ahmed on 2010-04-03
Thanks for God "ALLAH"
I have solved the problem 
the problem was that vdr can't access local network

I enable local network access for sound using "PAPREFS" which is sound access control application
and for image i must run xhost +  every time i logged in 

Can any one help me to make "xhost +local:vdr" run automatically when i logged in

or how to vdr to xserver access allow list permenantly

---

