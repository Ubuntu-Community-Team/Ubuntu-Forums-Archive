---
title: "Transfer files across wireless network"
date: 2011-11-20
forum: Networking &amp; Wireless
---

### Post by Garland Fox on 2011-11-20
Newbie needs help - searched to no avail - conclusion.
I have 3 computers on a wireless g network.
1. hp desktop dual boot win7 / 11.10 32bit.
2. Acer laptop dual boot Vista HP / 11.10 32bit.
3. Dell desktop with ONLY 11.10 32bit on it.

I need to share at least one folder on each computer with the other two - so I can freely transfer files and folders across the wireless network. >Independently from Windows<

Use no windows support-
Tried setting share in Nautilus - when I leave Nautilus folder loses share setting.
I know nothing of file sharing in linux.
What do I need?

Thanks for any assistance.

---

### Post by papibe on 2011-11-20
Here's an old [guide]("http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/"), but still valid.

Tell us how it goes.
Regards.

---

### Post by JayKay3OOO on 2011-11-20
You could try one of the other applications like gshare or something to see if you can get sharing up.

---

### Post by Dlambert on 2011-11-20
You could use drop box (depending on the size of the files. Not really permanent at all. Just temporary

---

### Post by Garland Fox on 2011-11-20
ok thanks -I am getting this moved to wireless and networking- I posted in wrong forum.

---

### Post by lechien73 on 2011-11-20
+1 @papibe

Personally, I used [this guide]("https://help.ubuntu.com/community/SettingUpNFSHowTo"). It's a bit more complex, but works perfectly for me.

If you feel comfortable with the command line, then this should work ok.

---

### Post by Garland Fox on 2011-11-20
I don't understand reference to windows networking - will samba work without windows?

---

### Post by Garland Fox on 2011-11-20
What is a drop box

---

### Post by Garland Fox on 2011-11-20
oops never mind - I will check it out

---

### Post by lechien73 on 2011-11-20
> **Garland Fox said:**
> I don't understand reference to windows networking - will samba work without windows?

Samba is generally used for networking to and from a Windows network.

For Linux -> Linux sharing, you can use NFS. How confident are you using commands in the terminal window?

---

### Post by ajgreeny on 2011-11-20
Transfer-on-LAN is very good and available from [http://code.google.com/p/transfer-on-lan/](http://code.google.com/p/transfer-on-lan/)

It is a cross platform java application which you download, extract the folder from the archive, then you can run it on ubuntu with the command ```
java -jar /path/to/folder/TransferOnLAN-0.4.4/TransferOnLAN.jar
``` which I have made into a launcher and put in my menus on 10.04.

---

### Post by Garland Fox on 2011-11-20
I have done some terminal commands - not extensive - but I can navigate slowly - about like my typing skills hah

---

### Post by Garland Fox on 2011-11-20
Thanks I will check out the TransferonLAN .
Being JAVA have any drawbacks?

---

### Post by Garland Fox on 2011-11-20
I will have to work on this more later - thanks for all the great ideas.
Other matter press till morning.

---

### Post by drs305 on 2011-11-20
Thread moved via OP request.

---

### Post by Garland Fox on 2011-11-21
Hello ajgreeny - the transfer on lan is looking good - I have run it on one computer and waiting to run it on the other 2. You mentioned having a launcher for the terminal command. When I had 10.04 I made launchers using the GUI and right click menu. In 11.10 I have not been able to figure out how to put a make a launcher for the desktop other than running the program and minimizing it to the Unity "launcher". Will figure it out somehow. Thanks for info.

---

### Post by ajgreeny on 2011-11-21
> **Garland Fox said:**
> Hello ajgreeny - the transfer on lan is looking good - I have run it on one computer and waiting to run it on the other 2. You mentioned having a launcher for the terminal command. When I had 10.04 I made launchers using the GUI and right click menu. In 11.10 I have not been able to figure out how to put a make a launcher for the desktop other than running the program and minimizing it to the Unity "launcher". Will figure it out somehow. Thanks for info.
Yes, it's a good program, and needs no real configuration;  all machines running it at the time are seen by the others, and nothing more needs to be done.

I can't help with your unity launcher problem, I'm afraid, as I have not been able to find it in me to continue using unity.  I keep looking and thinking it will get easier, but it does not, and everything I now do with a single click in 10.04, seems to take so much more effort to accomplish.

---

### Post by Garland Fox on 2011-11-21
I know the feeling on this Unity. I keep on trying. I will probably have to learn and make a bash script or something. I haven't got this working correctly yet - two of my machines have the same user name "garland" - but when the LAN program is running it is showing them up as separate users with each having their correct ip from the wan. Seems that part is OK. Haven't put it up on the 3rd machine yet.
QUESTION: All three machines would have to have the program running for the transfers to work. It doesn't run in memory does it?
Thanks much - I think it is going to work for what I need.

---

### Post by ajgreeny on 2011-11-21
You can install **alltray** and then run TOL in the background by putting it in the startup applications with the command ```
alltray <commandforTOL>
``` which will start TOL in the system tray as an icon.

---

### Post by Garland Fox on 2011-11-21
> **ajgreeny said:**
> You can install **alltray** and then run TOL in the background by putting it in the startup applications with the command ```
alltray <commandforTOL>
``` which will start TOL in the system tray as an icon.
I will check out the alltray. Somehow these computers see each other and once they transferred a file but it is not showing a transfer and the programs become unresponsive. 
You using ver 4.3 or 4.4?
 I don't know if 11.10 may have a firewall not letting it thru or something else going on.
Thanks for the alltray tip.

---

### Post by ajgreeny on 2011-11-21
I have TOL 4.4.

---

### Post by Garland Fox on 2011-11-22
[ATTACH]207774[/ATTACH]

Don't know why access denied
This from machine IP2 to #5, or other way = same result

Good morning--

---

### Post by Garland Fox on 2011-11-22
lechien73 many thanks 
ya taught an ol geezer a new trick.

---

