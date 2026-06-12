---
title: "Sharing UBUNTU Files"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by XWindows on 2010-09-21
Hello, sorry if this has been asked a couple dozen times. I have searched and attempted to follow the suggestions but after hours trying to resolve this I am stuck.

I have 10.04.1 UBUNTU installed on one computer with dual boot XP Pro, I have 3 other XP Pro computers connected to my network.

I have print share setup on the UBUNTU machine and CAN see and access the shared files on the 3 XP machines. I can surf the Internet with the UBUNTU machine. I can also Ping the UBUNTU machine from each of the 3 XP machines.

I CANNOT access the file shares on the UBUNTU machine from any of the XP's. File shares are setup, Samba and Nautilus is installed. I have tried to follow the instructions on modifying the smb.conf file but must not be doing it correctly. I get this same message from any of the XP machines when I try to connect to the UBUNTU machine. 

  [B]\\CYBERTECH-DESKOcybertech-desktop server (Samba, Ununtu) is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.
  The parameter is incorrect.[/B]
  
Any advice? Thank-You

---

### Post by jodlajodla on 2010-09-21
Read all posts in this thread -> [URL="http://ubuntuforums.org/showthread.php?p=9855996"]http://ubuntuforums.org/showthread.php?p=9855996
[/URL]

---

### Post by XWindows on 2010-09-21
I am pretty new to Linux. Is there a certain point in that thread I should be looking at. I have changed the WorkGroup to match my Windows network, MSHOME but then I got the message the Network Path was incorrect, so I changed it back and can again see the UBUNTU computer but still get the original error message when I try to access the system share.

Thanks!

---

### Post by Morbius1 on 2010-09-21
> \\CYBERTECH-DESKOcybertech-desktop server (Samba, Ununtu) is not accessible.There may be other things wrong but [COLOR=Blue]CYBERTECH-DESKOcybertech-desktop[/COLOR] is 17 characters too long.

The easiest way to fix it is through samba itself. Add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
netbios name = something
```Where [COLOR=Blue]"something[/COLOR]" is _less than or equal to 15 characters in length_.

Save the file and restart samba and see how much further you get:
```
sudo service smbd restart
```

---

### Post by Osamabingandhi on 2010-09-21
i just don't do anything anymore to get this working. You probably just missed something real simple. Firstly i just go to my homefolder and right click on the folder i want to share and there an alternative for sharing and i just click that one and voila! There you go! It just installs what you need and you do not need anything more! It is truly simply nowadays to use ubuntu. Almost no configuration on a newly installed system. I am so much more frustrated with windows when i am forced to use it(as autocad only works on windows)

Hope this answers your question!

---

### Post by XWindows on 2010-09-22
Thanks Morbius1, the name change of the computer was a big help. There was also an issue in the smb.conf regarding max allowed users, it was RMK'd and had a value %S. I can now see the Ubuntu from all 3 XP machines.

**One issue is that after about 4-5 hours the Ubuntu machine loses all connectivity. Cannot be Pinged or surf, reboot and all is good. It is wireless and the NIC is good with good signal strength.**


Thanks Osamabingandhi, I had done all the simple stuff, it was the computer name for sure.

---

