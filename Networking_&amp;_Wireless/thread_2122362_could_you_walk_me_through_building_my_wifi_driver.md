---
title: "could you walk me through building my wifi driver?"
date: 2013-03-04
forum: Networking &amp; Wireless
---

### Post by LGA45 on 2013-03-04
Okay. Here's where I'm at. I just installed Ubuntu 10.4 on my laptop.I've found a driver that will work with it, but it requires building. I have no idea how to do this. I got this driver:[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) and I need to know how to build it. I have a way to get a wired connection, but only in the day time. I do have my phone though. I can download and transfer files using that. 

Thank you in advance! :)

---

### Post by LGA45 on 2013-03-04
Anyone?

---

### Post by carl4926 on 2013-03-04
Why 10.04?

Does the laptop have a active wired connection?

---

### Post by LGA45 on 2013-03-05
I'm sorry... I don't know where I got 10.4... Its 12.10. And by active wired connection I assume you mean one that works, yes. I can use the internet when hooked to a wire. But I only have daytime access to a wire. (At the library)

---

### Post by carl4926 on 2013-03-05
Can you open a terminal and show me the result of this
```
lspci -nnk | grep -iA2 net
```

---

### Post by LGA45 on 2013-03-05
Here is how it responded. I hope an image is ok... [http://s1136.beta.photobucket.com/user/LGA45/media/Snapbucket/C88936B6-orig_zps06bc8d3c.jpg.html](http://s1136.beta.photobucket.com/user/LGA45/media/Snapbucket/C88936B6-orig_zps06bc8d3c.jpg.html)

---

### Post by carl4926 on 2013-03-05
OK
When you have a wired connection
Use your mouse to copy and paste this in to a terminal

```
[COLOR=#000000][FONT=courier]sudo apt-get install firmware-b43-installer[/FONT][/COLOR]
```

You may need to reboot once the above has finished installing

---

### Post by LGA45 on 2013-03-05
```
luke@Badass-bawler:~$ sudo apt-get install firmware-b43-installer
[sudo] password for luke: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-installer
luke@Badass-bawler:~$ 
```


This is the response. Is that error gonna be a problem?

---

### Post by carl4926 on 2013-03-05
Download this and extract the folder b43 and place it in your home directory
[http://dl.dropbox.com/u/10573557/b43_firmware/2013_b43/b43.zip](http://dl.dropbox.com/u/10573557/b43_firmware/2013_b43/b43.zip)

Now do this from a terminal

```
sudo mv b43 /lib/firmware
```

then reboot

---

### Post by LGA45 on 2013-03-05
Yeah, I'm now unplugged and on the Library wi-fi! thank you so much! :)

---

### Post by carl4926 on 2013-03-05
> **LGA45 said:**
> Yeah, I'm now unplugged and on the Library wi-fi! thank you so much! :)
Wonderful
Well done

---

