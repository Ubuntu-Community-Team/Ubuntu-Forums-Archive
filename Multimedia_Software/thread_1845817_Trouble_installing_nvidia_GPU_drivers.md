---
title: "Trouble installing nvidia GPU drivers"
date: 2011-09-17
forum: Multimedia Software
---

### Post by lanzd on 2011-09-17
Hello, I just upgraded to a nvidia GeForce GTX 560 ti video card and am  unsure how to install the drivers. I've seen another thread discussing  this issue but it is old and I need help following the steps.  And I'm  not even sure if it applies.  

The thread I've been reading is [http://ubuntuforums.org/showthread.php?t=1681040](http://ubuntuforums.org/showthread.php?t=1681040)

Now I've downloaded what I believe to be the correct driver for my card off of the nvidia site here [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

I chose GeForce 560 ti as the product, linux 32 bit, english US and get the file 

NVIDIA-Linux-x86-280.13.run

I've tried running the file in the terminal and it gives a message  saying it requires root access.  So I logged into root and ran the file  and then get a message saying I currently seem to be running an x  server, please exit x before installing.  

I'm not entirely sure what x is, from what I've been reading I think its  part of the gui interface for unbuntu.  But I have no idea how to exit  it.  Any relevant information I've found seems to involve temporarily  disabling the gui and I tried one method but It completely locked up my  system.  I then reinstalled ubuntu after deleting the old partition. (It  was a barebones install in the first place so I didn't lose anything).   

Thank you for any help.  And sorry if I'm a little dumb with this stuff.  I'm very new to ubuntu or even linux for that matter.

Dan

---

### Post by jawilljr on 2011-09-17
Why not install the drivers the easy way... using the x-swat PPA.

Type these commands in a terminal:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current libvdpau1
```

If there are no errors then just reboot.

Jerry

---

### Post by lanzd on 2011-09-17
Hello, thank you for the quick reply.  I ran the commands and after the 
```
sudo apt-get update
```

It gave me this error at the very end.

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by jawilljr on 2011-09-17
Do you have jockey or synaptic open.  If so the close it and try the "sudo apt-get update" again.

Also update-manager being open will cause the same error.

Jerry

---

### Post by lanzd on 2011-09-17
Allright, thankyou.  It is somewhat picking up my card now.  When I goto System -> Preferences -> monitor I get a message saying 

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server"

How do I run that file.

edit: I used the command 
"sudo nvidia-xconfig" and it gave an error saying it could not be found.  It
also said it created the file afterwards.  So I'm going to restart and see if it worked.

Thank you for your help so far.

---

### Post by jawilljr on 2011-09-17
Did you run the last command and reboot?  If so then run this at the terminal:

```
sudo nvidia-xconfig
```

Then reboot again.

What the above command does is give you a minimal xorg.conf file.

Jerry

---

### Post by lanzd on 2011-09-17
Yep that worked.  I now have my computer back.  

Thank you for all of your help.

---

### Post by jawilljr on 2011-09-17
Good... next time you in the Memphis area buy me a beer!

Anyway glad it is working. And please mark as solved.

Jerry

---

