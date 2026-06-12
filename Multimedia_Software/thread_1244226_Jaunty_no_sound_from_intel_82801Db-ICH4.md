---
title: "Jaunty: no sound from intel 82801Db-ICH4"
date: 2009-08-19
forum: Multimedia Software
---

### Post by toughy on 2009-08-19
Howdy all,

I am new to this forum and Ubuntu.  I loaded Jaunty on my Panasonic Toughbook CF-29 today.  I just installed a new HDD so decided to try out linux.

I have no sound (well very very weak sound, see below).  Everything seems to be working fine except for the sound.  I have spent the past 12 hours trying fixes from this forum and several others.  I have also run the full list of suggestions from the Ubuntu sound troubleshooting documentation with no success.

I have installed heaps of alsa packages and checked and rechecked all the settings suggested and nothing.  Until I tried UbuntuGeek's sound solutions.  After running all his suggestions I found that there was a very very very weak sound coming through the headphones.  If my house hadn't been absolutely silent I would have never heard it.

I have searched for my sound card in the forums and find no fix related to it.  If you know of one post the link please.

Does anyone have any suggestions?

Thanks
Brian

ps all my sliders are at 100% and I find nothing muted :confused:

---

### Post by toughy on 2009-08-19
bump!

Still no sound... If anyone can help it would be very much appreciated!

Thanks 
Brian

---

### Post by Yellow Pasque on 2009-08-19
You should try OSS4: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by toughy on 2009-08-20
Temüjin,

Ok trying that out but having some difficulties.


[LIST=1]
[*]when I ran the third command this was the result
[/LIST]
udah@judah-laptop:~$ sudo apt-get purge pulseaudio
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

     2.   When installing prerequisite packages the result was
 judah@judah-laptop:~$ sudo apt-get install -y binutils libgtk2.0-0 sed gcc libc6[sudo] password for judah: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


So does this mean that the host of these apps is down or is it my system causing this error?  Remember i am a newbie so be nice!

Thanks for the suggestion.  I did see my audio device on the list so here's hoping.
Brian

---

### Post by toughy on 2009-08-20
Yep as I suspected.  The server had been down.  downloading now.

Brian

---

### Post by toughy on 2009-08-20
Temujin

When I try to install the DEB file i get this error.  Please advise,


command (as per oss site you provided)

sudo dpkg -i oss-linux*.deb

dpkg: error processing oss-linux*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 oss-linux*.deb

I followed your purge from the link at the bottom of the page and tried a second time and still nothing.

thanks again

Brian

---

### Post by Yellow Pasque on 2009-08-20
Make sure you're in the right directory.

---

### Post by toughy on 2009-08-21
temujin,

I am unclear what you mean.  

How do I make sure I am in the right directory and if I am not how do I change it to the right directory.  And how do I determine what directory I am to be in?  

Sorry to ask you to specify in such detail but I am very new to this.  

btw I am originally from PA.  In New Zealand at the moment.

Brian

---

### Post by Yellow Pasque on 2009-08-21
Brian, are you using the pre-built .deb package or are you building from source?

---

