---
title: "Weird sound issues (sound partly broken 0_o)"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by Canesfan2020 on 2007-04-26
I was having a problem with sound not working at all in feisty but I was able to get sound working..except for the login menu..after I type in my username and pass sound starts working... any ideas how to fix it?

---

### Post by Canesfan2020 on 2007-04-26
Also, If I go to system ->administration -> login window and click play for the sound thats set there nothing plays

---

### Post by FishRCynic on 2007-04-26
if you are in gnome (ubuntu)
and using pulse audio  then this may work
i don't know if it would help with esd by itself

the bug report uses a method to test if the fix will work
i just put it in the file to make it work for me at logon 
...
appears there is a bug
whether it is gnome, esd or pulseaudio i am not qualified to judge

i do know that if i make a .gnomerc file in my home directory and add the line

ln -s /tmp/.esd /tmp/.esd-1000

i now have logon sound and system sounds.

this is slightly modified solution from a bug report

[https://bugs.launchpad.net/ubuntu/+s...io/+bug/108577](https://bugs.launchpad.net/ubuntu/+s...io/+bug/108577)

.....
after you make the .gnomeric file - logout and when you log back in you might
have system sounds

let me know if this helps or hinders

---

### Post by Canesfan2020 on 2007-04-26
that link is broken :(

Its only the sounds that play for login ready successful and failed login.. system sounds work. I was able to get it to work one time just buy checking and unchecking some boxes and then restarting but now its dead again.. It just seems odd that just the login menu sounds would be broken and nothing else :confused:

---

### Post by Canesfan2020 on 2007-04-26
fixed it.. xmms was the problem

---

### Post by Canesfan2020 on 2007-04-27
well..I thought.. its doing it again 0_o

---

