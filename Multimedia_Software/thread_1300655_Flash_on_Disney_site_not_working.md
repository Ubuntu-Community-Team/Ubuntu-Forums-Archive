---
title: "Flash on Disney site not working"
date: 2009-10-25
forum: Multimedia Software
---

### Post by timzak on 2009-10-25
Hi, I'm using Jaunty 64-bit with latest 64-bit Flash plugin from Adobe (10.0 r32).

This site seems to be stuck when loading Flash content:
[http://disneydigitalbooks.go.com/homepage.html](http://disneydigitalbooks.go.com/homepage.html)

If I fire up a Windows VM and surf to the same site in Firefox, it loads just fine.  I'm not sure if it's the site using Flash improperly, or the Linux version of Flash itelf.

Any suggestions?  Can someone in Jaunty 32-bit test the site out and see if it works for them?  I'm curious if it's a 64-bit issue too.

Thanks,
Tim

---

### Post by hansdown on 2009-10-25
Hi timzak.

All of that site works on my jaunty.

If you search synaptic for flash, you can check if```
 flashplugin-installer
``` is running.

---

### Post by timzak on 2009-10-25
hansdown,

Are you running 32-bit or 64-bit?

Thanks for your reply.

edit:  there's a swirling oval in the center of the screen that should eventually go away when the page finishes loading.  My screen never leaves the oval in the center.

---

### Post by hansdown on 2009-10-25
I'm running 32-Bit.

My browser takes a couple seconds to change to the screen in the screen shot.

I can then click on all links.

---

### Post by markbuntu on 2009-10-25
It works for me on 64 bit Jaunty. It asks me to register to read the books.
OOPs, I am not on jaunty at the mo, stand by....

EDIT: OK, I am on Jaunty 64 bit, the site loads just fine, sound effects and all.

---

### Post by timzak on 2009-10-25
Hmmm...must be my implementation of 64-bit Flash.  Here's how I installed (and it works for everything else except this site):

Downloaded 64-bit Linux Flash from:
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

extract libflashplayer.so file to /home/tim/.mozilla/plugins

Done.  That's it.  So far (since Jaunty was released in April) this has worked for every Flash site I've visited.

Any ideas?

---

### Post by hansdown on 2009-10-25
I just checked my firefox plugins.

Maybe try installing divx web player plugin.

Sorry, I'm grasping at straws here.

---

### Post by timzak on 2009-10-26
No problem, thanks for trying.  I already have that plugin enabled.  Still can't get the site to work.

Incidentally, I've got the same problem on two separate systems, both running Jaunty 64-bit, both with Flash installed the same way.  One's a laptop, the other a desktop.

Weird.

Any other ideas greatly appreciated!

Tim

---

### Post by markbuntu on 2009-10-26
The flash I am using is from ubuntu-restricted-extras.

---

