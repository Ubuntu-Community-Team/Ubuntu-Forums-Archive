---
title: "Syncing iPhone in iTunes? Simplest way?"
date: 2009-04-23
forum: Multimedia Software
---

### Post by Gizim on 2009-04-23
Just installed Jaunty and trying to make the full switch from Windows to Ubuntu but I own a iPhone that is NOT jail broken. Wondering what is the simplest way to get it to sync to download new podcasts and do backups? I have heard people getting iTunes 7.6 to work in Wine. But i'm wondering if it would be simpler to just have a small Windows partition for this.

---

### Post by aeiah on 2009-04-23
have a look here: [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

i dont know whether you need to jailbreak your phone or not for some of those solutions. obviously you might want to skip the first section since a windows virtual machine should really be a last resort and focus on whichever out of sections 2, 3 or 4 is most appropriate.

---

### Post by Gizim on 2009-04-23
> **aeiah said:**
> have a look here: [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

i dont know whether you need to jailbreak your phone or not for some of those solutions. obviously you might want to skip the first section since a windows virtual machine should really be a last resort and focus on whichever out of sections 2, 3 or 4 is most appropriate.

I wouldn't mind doing a VM Box if it works i only connect it to xfer some new music and update my podcasts and still i do that rarely.

---

### Post by rreyes1316 on 2009-04-25
So what did you decide to do GIZIM? Did you look at the aeiah link? I am having one heck of a time trying to get the usb recognized in VBox. I may just have to dual boo for a while. 

Send me a message if you get any answers. I will continue to try.

---

### Post by TjankMjaster on 2009-04-26
I've been testing Jaunty on liveCD...  only thing tying me down to Winders' is itunes for my ipod.   anyone used RythmBox or the other ipod compatibles?  Do they support syncing Video formats?

---

### Post by n8wood on 2009-04-27
I spent some time on this trying to come up with a decent solution for syncing the iPhone on Linux. I came up with something that uses VirtualBox command line stuff with udev. It works quite well.

When I attach my iPhone via USB, VirtualBox automatically starts the Windows virtual machine; after Windows boots the phone automatically syncs. When I disconnect the iPhone, VirtualBox automatically shuts down the VM cleanly.

I posted the details here: [http://n8wood.wordpress.com/2009/04/22/iphone-syncing-and-linux/]("http://n8wood.wordpress.com/2009/04/22/iphone-syncing-and-linux/")

---

### Post by Dr.Vista on 2009-04-27
> **n8wood said:**
> I spent some time on this trying to come up with a decent solution for syncing the iPhone on Linux. I came up with something that uses VirtualBox command line stuff with udev. It works quite well.

When I attach my iPhone via USB, VirtualBox automatically starts the Windows virtual machine; after Windows boots the phone automatically syncs. When I disconnect the iPhone, VirtualBox automatically shuts down the VM cleanly.

I posted the details here: [http://n8wood.wordpress.com/2009/04/22/iphone-syncing-and-linux/](http://n8wood.wordpress.com/2009/04/22/iphone-syncing-and-linux/)
Looks great, I'm going to try it later.

---

### Post by TjankMjaster on 2009-04-28
> **n8wood said:**
> 
I posted the details here: [http://n8wood.wordpress.com/2009/04/22/iphone-syncing-and-linux/](http://n8wood.wordpress.com/2009/04/22/iphone-syncing-and-linux/)


Cool Thanks.  I haven't experienced VBox yet, but will look into this.

---

### Post by rreyes1316 on 2009-05-07
Did you ever get a solution for your iPhone? I jailbroke my phone just to get it going with ubuntu. And I got to tell you . . .it is better that any firmware upgrade in the near future--it simply rocks!!! After that I suffered long nights trying to get it to sync with every media player out there--it totally sucked and my eyes and head still hurts. Well guess what! I finally got it to sync wirelessly with Amarok. I got rid of the current Amarok and installed the 1.4.10 version; It is so much better. I have no idea why they made it crappy. (Heres the link [http://nomad.ca/blog/2009/apr/3/amarok-14-jaunty-ubuntu-904/](http://nomad.ca/blog/2009/apr/3/amarok-14-jaunty-ubuntu-904/) ).

Anyway, let me know how your progress is.

---

### Post by jbryant803 on 2009-11-27
I just purchased an iPhone 3Gs, which i'm completely in love with and refuse to give up or "jailbreak" to void my warrenty, and was wandering if there are any real solutions for ubuntu 9.10. For the last two days i've been trying out many so called solutions on this forum to no avail, and am starting to get frustrated. No offence but please check your info before trying to help, i've really enjoyed my switch to ubuntu but any os is only as good as the programs it allows us to run. That's why I left Windows in the first place and don't want to go back even in a dual boot environment, so if anyone knows of a solution for ubuntu 9.10 or one planned in the future I would love to know.

---

### Post by balloooza on 2009-11-27
For now it is esiest to use itunes on mac or windows, but the ubuntu comunity seems to be hard at work on the iphone support.

and BTW, jailbreaking dose not void your warenty, if you need to send it back in you can flash it with itunes. I have never done it, but I hear that it is awsome.

Mark

---

