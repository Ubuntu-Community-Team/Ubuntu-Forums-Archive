---
title: "mount and share when booted"
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by richyrichuk on 2011-03-15
hi guys, u will have to excuse me not all up to date with ubuntu

in a nutshell im trying to share 2 HDD's in same machine with several windows machines

1. auto login so no welcome screen.
2. auto mount the drives
3. share the drives with/without password 

1 is fine, i did resolve issue 2 with "storage device manager" but no matter what i do i cant get it to load correctly as i cant remove the option "mount file system in read only mode" so i cant create/move/delete anything. i did also change the owner for when it mounts off root to my user, but still no avail.

and i can share the drives using ubuntu, but i also have samba.

**not important**
```
also another 2 Q's for after i have sorted this, i need ubuntu to shut down when i simply
 press the off button as this will have no mouse, keyboard or TFT attached.
so then i can simply press the on button and within a min or so i can just connect to my
 'network drives' and then also to enable a remote desktop viewer, i did try the inbuilt 1
 but couldnt connect with my win 7 machines.
```


using: Ubuntu 10.10

---

### Post by richyrichuk on 2011-03-16
can anybody point me in the correct direction please.

---

### Post by richyrichuk on 2011-03-29
could i get a little help please?

---

### Post by 123.jack.scott on 2011-03-29
What sort of HDDs are they, internal?

---

### Post by 123.jack.scott on 2011-03-29
And as with your "Not Important" You could use the command
```
sudo shutdown -h now
```
via ssh.

---

### Post by collisionystm on 2011-03-29
Ok just to understand. you have ubuntu 10.10 with 2 hard drives installed that you need to share with windows machines?

Easy.

In the gui, just right click on the drive and go to sharing

enable sharing, guest access. Ubuntu downloads needed samba software. DONE.

Now from windows just browse to your computer with start, run, \\<ipaddressofubuntu>

Right click on the shared folder, map network drive. done.

You can shutdown ubuntu from ssh using putty on windows. Just ssh to your ubuntu, type shutdown -P 0   ( capital P)

of course you will need to physically hit the button to power back on.

---

### Post by richyrichuk on 2011-03-30
hi guys, thanks for the replys

yes exactly what im trying to do collisionystm.

i found the option for the machine to power off under 'power management' when the off button is pressed, default is to 'do nothing'

i couldn't find the 'share' option when right clicking on the drives, so i have had to share a folder on the drives, but i have simply put everything into there (close enough for what i wanted)

and putty in windows u can do a remote shutdown yeah? cool good stuff.

yes they are internal 123.jack.scott its a mini HP server, so they are in non-hot-swappable bays.

only issue i still stand with is the remote desktop, logmein doesnt support linux yet, only a beta ver. and again i still struggle with the inbuilt software.

cheers

rich

---

### Post by kd4dii on 2011-03-30
Hi
     For the remote problem try VNC,  Its in synaptic.  Install it on both machines and run the remote desktop program from system preferences.  Use the ip address of the one you want to log in to and it is as if you were at the other machine.
     Hope this helps.

Bob

---

### Post by richyrichuk on 2011-03-30
brill, i'll try VNC, wasnt a big fan when i used last, was a few years ago mind u.

through latest VNC cna u only do it through IP? just it means either give it a static Ip to make sure i get it, or run ping test to confirm IP each time.

can i not get remote desktop built into ubuntu to work through 7? or is it simply to much work, i'll accept it, if it is. just a thought as its there.

---

