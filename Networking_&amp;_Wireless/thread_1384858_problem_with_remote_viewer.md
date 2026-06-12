---
title: "problem with remote viewer"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by destroyerzx1 on 2010-01-18
ok so I got remote desktop setup on my friends computer so that I could help him out from my house instead of driving into town all the time. I can connect and move the mouse around but when I click on stuff it doesn't do anything, it does on his end but mine doesn't refresh and show me anything. I have to exit and restart the connection to see the update. how do I fix that?

---

### Post by johnson.d on 2010-01-19
You can try the following to find what the problem is

1) If Desktop effects are enabled in the remote system, disable them for testing purpose. I have seen many people complaining about similar problem with desktop effects being enabled.

System-> Preferences-> Desktop effects

2) Check whether the network has consistent connection, as network inconsistency can lead to such problems.

3) Try stopping other programs that utilize the bandwidth of the connection on both the machines for testing purpose.

4) Can try using other remote desktop clients like Real VNC to check if this issue is specific to the client software.

---

### Post by toogooda on 2010-02-04
I have the same issue and will try without desktop effects and post back

---

### Post by doas777 on 2010-02-04
there are a couple of workarounds if you don't want to abandon desktop effects:

1) you can turn off compiz (desktop effects) with this line of shell:
```
metacity --replace
```so if you login and cant' get any updates, then hit alt+F2, and type the line blind. after you hit enter, disconnect and reconnect, and you shoudl see screen updates. you can also run the line via an ssh session if you want to do it before trying to connect

2) call vncviewer with teh -nodamage switch
eg:```
vncviewer -nodamage <remotehostnameorip>
```this however increases the bandwidth consumption for vnc and slows things down a bit, since it updates the entire screen, not just the parts that change.

here is some more info on the topic:
[http://ubuntuforums.org/showthread.php?t=421272](http://ubuntuforums.org/showthread.php?t=421272)


Personally i don't use ubuntus "remote desktop" vnc anymroe, instead favoring freeNX. it's much better for my usecase.

---

### Post by toogooda on 2010-02-05
> 
Personally i don't use ubuntus "remote desktop" vnc anymroe, instead favoring freeNX. it's much better for my usecase.Thanks for the help, Is there a fix for this on the way?
does freeNX have the same issue?

I tried turning off desktop effects and it solved this issue instantly, didn't even have to reconnect!

---

### Post by doas777 on 2010-02-05
> **toogooda said:**
> Thanks for the help, Is there a fix for this on the way?
does freeNX have the same issue?

I tried turning off desktop effects and it solved this issue instantly, didn't even have to reconnect!


nope, the problem does not affect freenx. the big differance between nx and vino (ubuntus vnc) is that it cannot share a session with teh desktop user, but instead presents a new resumable session. it's also faster and doesn't seem to get bogged down when you move too fast. it also scales the screen output to the clients specs. vnc gives you the native resolution on the remote host, which can be a pain when connecting from a laptop to a media box running at 1920x1080.

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

