---
title: "[SOLVED] How Do I Uninstall Realplayer 11?"
date: 2008-08-31
forum: Multimedia Software
---

### Post by r4wj4 on 2008-08-31
I downloaded realplayer 11 which was a .bin file. Made that into a executable file(using chmod +x) and installed it. Now I want to uninstall it and there is no entry of it in synaptic(because manually installed). How do I uninstall it...any advice?

I'm a ubuntu/linux noob.

---

### Post by ranjithnair on 2008-09-01
Try this ```
sudo dpkg -r realplayer
```
If the above does not work then try removing manually. Realplayer only installs a binary file named realplay, its icons and some more, not a lot. Just type:
```
locate realplay
```
Here how u remove it manually:
In Linux, open a Terminal (Applications->Accessories->Console (or Terminal)) and go with the command "cd" to each directory where the file is. Then, to remove it type:```
sudo rm -f nameofthefile
```
If it is a directly then:
```
sudo rm -rf nameofthedirectory
```

---

### Post by r4wj4 on 2008-09-01
I found where its installed...its in /opt/real/RealPlayer. I just deleted that directory, but whenever I right click on a video file it still has the option to  play it with realplayer...or whenever you set the file to open with a certain program real player it still a option. The icon still shows under Application>Sound & Video. How to I completely remove it.

"locate realplay" gave me 57 entries of all the reaplyer stuff...do i have to manually remove all of them?

thanks.

---

### Post by r4wj4 on 2008-09-05
bump

---

### Post by gonzomalan on 2008-09-29
even though it says solved, i'm going to post my opinion that yes, you need to uninstall each file. and there are many. i am in the process of doing this myself and came across this entry.

---

### Post by JGable98 on 2009-01-28
This is what worked for me

> sudo dpkg -r realplay 11.0.1.1056

---

### Post by jrusso2 on 2009-01-28
Usually .bin files have an uninstall script.  Why don't you run that it should be in a directory close to the program which is /opt I think for realplay.

---

### Post by simptechmike on 2009-02-18
> **JGable98 said:**
> This is what worked for me


Thanks. This worked for me as well!

---

### Post by juan.manuel.melillo on 2009-05-30
> **r4wj4 said:**
> I found where its installed...its in /opt/real/RealPlayer. I just deleted that directory, but whenever I right click on a video file it still has the option to  play it with realplayer...or whenever you set the file to open with a certain program real player it still a option. The icon still shows under Application>Sound & Video. How to I completely remove it.

"locate realplay" gave me 57 entries of all the reaplyer stuff...do i have to manually remove all of them?

thanks.

I did the following in same situation. Be carefull, an error would mean you lost your information. :o

locate realplay | xargs sudo rm -rf

Juan Manuel

---

### Post by eazely on 2009-09-19
Steps at [http://eazely.com/archives/tinker/875]("http://eazely.com/archives/tinker/875") worked for me on a 'manual' installation. Don't know if the uninstall scripts are there in a .deb installation though

---

### Post by gchatzim on 2010-04-12
THis is the automatic uninstall that what worked for me:

$ sudo -i
# /opt/real/RealPlayer/postinst/postuninst.sh
# rm -rf /opt/real/RealPlayer/

from
[http://ubuntuforums.org/showthread.php?t=920171](http://ubuntuforums.org/showthread.php?t=920171)

---

### Post by myhieu on 2010-06-04
```
sudo dpkg -r realplay
```

works well on Ubuntu 10.04

---

### Post by opiumpoetry on 2011-03-21
sudo dpkg -r realplayer

this one did **not** work 4 me.

---

### Post by opiumpoetry on 2011-03-21
sudo dpkg -r realplay 11.0.1.1056

this one **did** work 4 me.

---

