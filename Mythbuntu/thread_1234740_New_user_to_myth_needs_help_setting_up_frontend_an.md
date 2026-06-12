---
title: "New user to myth needs help setting up frontend and recording with backend"
date: 2009-08-08
forum: Mythbuntu
---

### Post by derrick1985 on 2009-08-08
Hi,

i'm a new myth tv user and I am in need of a little help. I got the frontend/backend installed on the same machine, and is working (I can actually see the TV) but i'm not sure on how to set up a few little things.

1) I would like to be able to also use the PVR function of the mythbox from my windows machine, with a different frontend (boxee). I tried putting the myth:// shortcut in (myth://rockwelltv:rockwelltv@rockwelltv) but I can't see any of the live channels at all. 
2) When I tried to schedule a recording through mythweb, I got error 255, not sure what is going on there.
3) How can I set up the myth frontend, on the same machine as the backend, to also view files and play them from my windows shares?

Thanks,

---

### Post by mitchell2345 on 2009-08-08
1. you must enable the MySQL server to be accessible via the network.  In MCC goto: System Services and enable MySQL Service.

2. not sure.  can you post more of the error?

3. you will need to mount the samba shares on your mythbox.
[http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html](http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html)

After you can view the files on your Mythbox you need to add the directory to MythVideo.  Make sure you have the plugin installed in MCC.  Then goto settings in mythfrontend and add the directory you created above.

~Mitchell

---

### Post by derrick1985 on 2009-08-09
> **mitchell2345 said:**
> 1. you must enable the MySQL server to be accessible via the network.  In MCC goto: System Services and enable MySQL Service.

2. not sure.  can you post more of the error?

3. you will need to mount the samba shares on your mythbox.
[http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html](http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html)

After you can view the files on your Mythbox you need to add the directory to MythVideo.  Make sure you have the plugin installed in MCC.  Then goto settings in mythfrontend and add the directory you created above.

~Mitchell

Thanks for the info, I was able to get 1 and 3 sorted out.

As for the second one, when I try and transcode a video from mythweb, it always errors out. This link shows it. [[IMG]http://i933.photobucket.com/albums/ad171/derrick1985/th_mythtv.jpg[/IMG]](http://s933.photobucket.com/albums/ad171/derrick1985/?action=view&current=mythtv.jpg)

Also, one last thing, for that 10 minute clip to show this error, it took up a little over 100mb of space, is that normal, or is there a way to tone that down a bit, so each 30 minute show is roughly only 150mb? It is only SD signal.

---

