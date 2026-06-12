---
title: "Samba, smbclient and Gigolo"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by mechanic on 2010-12-28
Lxde is giving me some problems with browsing network (Windows) shares; on my machine the file manager won't show local network servers and Gigolo doesn't show the network tab (!) so it's hard to search network machines for shared folders and files. Trying the same machine with live-CDs (eg Knoppix) works fine, the same version of Gigolo shows the network tab and I can browse windows shares ok. The basic samba stuff is working, I can see the machine from others using file managers and I can transfer files from there, but I'd really like to get this Lubuntu machine working well - I like the lxlauncher interface! smbclient and smbtree show the local network ok as far as I can tell, it's just the file manager and Gigolo on Lubuntu.

Any suggestions as to what to do to get these GUI applications to work with smb?

---

### Post by mechanic on 2010-12-29
Thanks for the volume of response!:p But for completeness and to suggest a work-round for anyone in the same boat, I tried (on the advice of my friend on here) to get over this by installing some Gnome components to see if that added the necessary networking tools. I installed gnome-core and voila! Gigolo started working properly and I was able to mount some shares from there in the usual way - and it connected with Pcman file manager properly too. Re-booting showed that I could open a Gnome session, but opening the favoured Lxde session using lxlauncher worked as well as before. If anyone has a clue what is happening here I'd be interested, otherwise I consider the issue SOLVED.

---

### Post by fabio_floripa on 2010-12-30
Hi, I installed lubuntu and I am having the same problem I dont know how to browse my network. pc with windows can see me on network neigborhood but I have no idea how to "see" them once lubuntu does not have de "network shortcut".
Could you help me to get it done? I am sourching for days, I made a lot of changes on terminal but nothing happen.

I have no idea what is gigolo but i will try it too.. actually i will try to try if you what I mean!

---

### Post by mechanic on 2010-12-30
It usually takes a bit of fiddling to get Samba to work properly but here are the main steps that work for me:

1. Install samba, smbclient on the Ubuntu machine

2. Run 'sudo smbpasswd -a <username>'
   - usually best to keep the same username and password everywhere to make this work, and you must have a Linux user account with the same name as you use with Samba.

3. Sort out the /etc/samba/smb.conf file - make sure the 'workgroup' variable matches the computer properties and you use the same value on all the machines on your network - probably not essential but it speeds things up! Also check the value(s) on the 'interfaces' line, is it the same as shown when you run 'ifconfig', e.g. eth1 or wlan1 or whatever.

4. Run 'sudo /etc/init.d/samba restart' .

5. Check the values in the /etc/hosts file, add lines for all the machines on the network if you can.

6. You may need to add these lines to /etc/samba/smb.conf :
    netbios name = <machine hostname>
    name resolve order = lmhosts wins bcast host

7. Test things by running 'testparm' (not as root, in your normal account), which checks the smb.conf file; 'smbclient -L <hostname or IP address of another machine on the network>' ; smbtree  (shows the smb servers on the network, and gives a clue as to which ones are giving problems.

8. On Windows machines and Linux ones too, reboot often to get it all to start properly, run n. 4 above to register any change on your Ubuntu machine.

9. On Ubuntu, nautilus should show the WORKGROUP network and you can browse from there (menu -> Go -> Network -> Windows Network . On Lubuntu I found it best to install gnome-core as described above.

 - Good luck!

---

