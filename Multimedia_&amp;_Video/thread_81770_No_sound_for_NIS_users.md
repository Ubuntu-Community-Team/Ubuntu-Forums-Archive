---
title: "No sound for NIS users"
date: 2005-10-25
forum: Multimedia &amp; Video
---

### Post by fouad on 2005-10-25
In several same machines my users who belong in audio group have no problem to use audio.

For perople who logon with NIS the audio not work.

The solution of this problem can bee: 
-adding all users from NIS server in audio group  in each machine.

I have 24 machines and 500 users so it's not easy solution

Do you have another idea ?

Thanks

#lspci
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

/proc/asound # cat cards
0 [ICH            ]: ICH4 - Intel ICH
                     Intel ICH with AD1981B at 0xdfebfe00, irq 23

---

### Post by eagle on 2005-11-27
In the /var/yp/Makefile  set the mingid=1 instead of 100 and then the sound e.d will work
:p

than the users on the server must be members of the audio video group etc......

---

