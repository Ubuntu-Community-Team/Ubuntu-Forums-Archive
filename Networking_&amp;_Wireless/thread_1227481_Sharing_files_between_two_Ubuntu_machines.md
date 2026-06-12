---
title: "Sharing files between two Ubuntu machines"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by mvelte54 on 2009-07-30
I am running two Ubuntu machines both running 'Jaunty Jackalope' I am trying to share files beween the two of them over my home network.

I have tried installing samba, and after trying several attempts to connect the two no luck. 
I then tried 'OpenSsh' and then tried to connect using the ip address of the other computer through port 22, 'timed out' is the response I get from the machine.

If it matters I do have 'Firestarter' running. There's got to be an easier way...
Any help would be much appreciated. :confused:

---

### Post by VipX1 on 2009-07-30
Firestarter caused me problems so I changed to Guarddog because it has a feature that allows you to switch it off so you know if it is the firewall that is causing the problem. I would imagine Firestarter should have some way of switching off too. Switch it off and try to connect. If it works then you know the cause.
Create a folder in the home directory and call it 'public'. Right click on it it and share it also under the name public.. You might need to install sharing and then restart your computer..
You should be able to click on Network and see the other computer and then by clicking on that you will see the shares. 
Do that first bit and I'll check how I did the second bit and come back to you..

---

### Post by mvelte54 on 2009-07-30
Thank you I'll try that. Now that I think of it I think I did turn off Firestarter on this machine but not the other.

---

### Post by mvelte54 on 2009-08-01
Well that didn't work I shut down 'Firestarter' on both machines.
I can connect to either machine which gives me a desktop shortcut called, 'ftp on 192.168.1.101' or '192.168.1.100' on the opposite machine but when I open it I see 'Shared files' on either machine. 
I can't drag and drop a file into the folder as it is not the right file type. Whether it be a .jpg a or even an mp3. I have to send it to the folder via tar.gz. I can do that from either machine back and forth or so I thought. When I look for them in the 'Shared file' on the opposite machine it's just not there however it is in the shared folder on the host machine? I have configured 'Firestarter' to allow traffic between each other machine and I am  using samba and have tried connecting via ftp. Both machines share the same password and login and I am sharing the Internet through a Dlink router.

Obviously I'm not doing something right. Can anyone recommend a site or have the patience to walk me through this? I have read the Ubuntu- wiki on 'Firestarter'. :confused:

---

### Post by mvelte54 on 2009-08-02
I just wanted to thank you VipX1. 
I took your advice after struggling here for several days and installed 'Guarddog'. What a breeze it was to configure. I then tried to connect the machines and found that I still couldn't?!? 
I then changed the name of my home directories as they were both the same for example they were both named '/home/marty/'.
I then made my home directories 'Shared folders' and now happily I can see what's on either machine from the other, even run programs from the opposite machine. One thing I haven't worked out yet is moving files from one to the other. 
Thanks to you I am one step closer. 
I am very grateful for your guidance.
:popcorn:

---

