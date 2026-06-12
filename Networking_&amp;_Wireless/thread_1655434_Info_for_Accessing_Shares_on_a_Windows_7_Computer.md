---
title: "Info for Accessing Shares on a Windows 7 Computer"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by pgn674 on 2010-12-29
I just got my Ubuntu 10.10 laptop to finally be able to access my Windows 7 Professional's shares, and I'd like to share how I got it working.

Whenever I would go to Places > Network on Ubuntu, and then double click on my Windows computer (sometimes after finding it in Windows Network > {workgroup name}), it would immediately bring up a box saying "Password required for {computer name}". My Windows password wouldn't work here, but I didn't even want to be asked for a password. In Windows, under Network and Sharing Center > Choose homegroup and sharing options > Change advanced sharing settings..., Turn off password protected sharing was already selected.

So, I eventually found out that samba (the program Linux uses to talk with Microsoft's SMB network share protocol) has a [bug]("https://bugzilla.samba.org/show_bug.cgi?id=7577") of sorts. The format of the SMB packets coming from a clean Windows 7 is known by samba. However, if you install Windows Live Sign-In Assistant (which is provided through Microsoft Update) on Windows 7, the packets coming from Windows 7 are modified, and samba can not handle this. A patch has been written for samba, but Ubuntu's repositories (which has samba version 2:3.5.4~dfsg-1ubuntu8.1) does not yet have that patch.

Also, it seems Microsoft has stopped Windows Live Sign-In Assistant from appearing in Programs and Features. It doesn't appear even if you specifically [download]("http://www.microsoft.com/downloads/en/details.aspx?FamilyID=9ba199ef-3086-4f12-970d-8745be104600") and install it separately. I did, however, notice that the installer calls itself Windows Live Essentials 2011. So I found that in Programs and Features, and uninstalled it. It asked which components I wanted to uninstall, and I selected all of them. Rebooted Windows, and now I can access the share no problem.

I also grabbed the offending packet using Wireshark before and after that uninstall. The packet is indeed different. Specifically, without Windows Live Essentials 2011, there is no mechToken in the packet.

The current version of samba [available]("http://www.samba.org/") is 3.5.6. I may try downloading and compiling that later, and see if it deals with the change that Windows Live Essentials 2011 makes OK.

Also, it may be possible to get the share working without uninstalling every single Windows Live Essentials 2011 component. You may want to try that if you would like to keep a component.

---

### Post by pgn674 on 2010-12-31
Alright, I just found that I can't access my Windows 7 shares again, after rebooting Windows a few times. I look in Programs and Features, and lo and behold, Windows Live ID Sign-in Assistant is there now. Windows Live Essentials 2011 is not. I have not idea how Windows Live ID Sign-in Assistant appeared, but I'm uninstalling it now.

So it looks like we have to look for both programs now. Maybe periodically, or maybe just every time it breaks.

---

### Post by PatchesTheCaveman on 2010-12-31
Thanks for figuring this out!  Quite a few people have run into this problem in the last few days.

---

### Post by pgn674 on 2011-01-01
I figured out why Windows Live ID Sign-in Assistant appeared (and it did a few times for me). There's a Microsoft Update, marked as Recommended in the Important section (meaning it wants to install when you shut down your computer) called Games for Windows Software V3.4. Installing this installs Windows Live ID Sign-in Assistant too. So, I found and uninstalled Microsoft Games for Windows - LIVE and Microsoft Games for Windows - LIVE Redistributable in Programs and Features. This stopped that update from appearing. I tried reinstalling Windows Live Essentials 2011 to see if sharing would still work, but it broke.

So, in conclusion so far, you must uninstall all of these:

Windows Live Essentials 2011
Windows Live ID Sign-in Assistant
Microsoft Games for Windows - LIVE
Microsoft Games for Windows - LIVE Redistributable

After uninstalling one and rebooting, another may appear, so be sure to check.

Oh, and it looks like compiling and installing samba from source isn't as simple as ./configure, make, sudo make install, and samba doesn't provide a .deb installer, so I guess I'll need to wait until an updated samba is pushed to Ubuntu's repositories.

---

### Post by PatchesTheCaveman on 2011-01-01
There are a couple of extra steps needed to build Samba, but it's nothing too complicated.  Just follow the instructions at [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/compiling.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/compiling.html)

---

### Post by RickAN on 2011-01-03
Hi All,

This problem has been a frustration for me also. I'm a complete Linux/Ubuntu/SMB n00b but I finally found a soultion that worked in the REDHAT bug forums.

[https://bugzilla.redhat.com/show_bug.cgi?id=651722](https://bugzilla.redhat.com/show_bug.cgi?id=651722)

Basically you add client use spnego = no the smb.conf and restart smbd. As soon as I did that - up came share access. There was no need for me to screw with WLE 2011 at all.

Hopes this helps someone.

-Rick

---

### Post by mordanda on 2011-01-04
Just to clarify, you just need to add the line:

client use spnego = no

to /etc/samba/smb.conf

right?  Is there anywhere in the file it needs to go, and section?

Dan

---

### Post by Aearenda on 2011-01-04
I added it into the global section near the top of smb.conf, restarted smbd, and it's working!

NB, there may be some scenarios this will break rather than fix.

---

### Post by floorish on 2011-01-06
Hurray, "client use spnego = no" worked for me as well!

Thank you very much for the solution, it bugged me for months.

---

### Post by florus on 2011-01-06
It worked for me too. Many thanks.

---

### Post by mstrelan on 2011-01-11
This didn't work for me. Ubuntu 10.10 64 bit, Windows 7 Ultimate. Even did a full reboot. Just keeps asking for password even though this share is publicly accessible.

I have no issue connecting to a Vista machine

---

### Post by mikk123 on 2011-01-13
[SIZE=2]Hi.
I was having the same problem. I'm am using Ubuntu 10.04 LTS 64bit. The Windows 7 machine that i need to access is not my, so I had to resolve the problem acting only on my linux box. Solutions reported previously in this topic and others suggested changes to smb.conf that I found in others forum didn't worked for me.
Finally I solved the problem installing more recent packages for samba. I manually downloaded samba and sambaclient packages for the natty(ubuntu 11.04) release from [here]("http://packages.ubuntu.com/"),  I downloaded also all packages necessary to fulfill dependencies, and installed them with 
#dpkg -i *.deb
This made smbclient work, but browsing network from nautilus was still broken.
Then I download and installed latest(natty) gvfs and gvfs-backends packages, with all dependencies, and this fixed problems in nautilus too.
Maybe this is not a "clean" solution but it worked, and I didn't needed to change smb.conf or windows configuration.
Sorry if my English is not very good.

This is the complete list of packages I installed:[/SIZE]
[SIZE=1]libpopt0_1.16-1_amd64.deb
libsmbclient_3.5.6~dfsg-3ubuntu3_amd64.deb
libtalloc2_2.0.4-1_amd64.deb
libwbclient0_3.5.6~dfsg-3ubuntu3_amd64.deb
samba_3.5.6~dfsg-3ubuntu3_amd64.deb
samba-common_3.5.6~dfsg-3ubuntu3_all.deb
samba-doc_3.5.6~dfsg-3ubuntu3_all.deb
smbclient_3.5.6~dfsg-3ubuntu3_amd64.deb
swat_3.5.6~dfsg-3ubuntu3_amd64.deb (only needed if you use swat)

For nautilus:
gvfs_1.7.0-0ubuntu1_amd64.deb
gvfs-backends_1.7.0-0ubuntu1_amd64.deb
libglib2.0-0_2.27.91-0ubuntu1_amd64.deb
libgphoto2-2_2.4.10.1-2ubuntu4_amd64.deb
libgphoto2-port0_2.4.10.1-2ubuntu4_amd64.deb
libimobiledevice1_1.0.4-1build2_amd64.deb
libjpeg62_6b1-1_amd64.deb
[/SIZE]

---

### Post by RickAN on 2011-01-21
::sigh:: Here we go again. I received about 20 updates today - some were for Samba - the descriptions specifically addressed the Win 7 share issue. 

I restarted after the update and tried accessing the share with the 'client use spnego = no' still there and also with it removed.

Well, either way - I can access the share - but - not with Nautilus. I can use 'connect to server' specifying the netbios name and share name - connects fine, mounts and is then accessible via nautilus like any other mounted file system. However using the 'network' option is broken.    

I suspect that mikk123's solution of updating gvfs would solve the problem - but at the moment - I'm in no mood.  :???:

---

### Post by pgn674 on 2011-01-21
I just checked and saw that samba 2:3.5.4~dfsg-1ubuntu8.2 (replacement for 2:3.5.4~dfsg-1ubuntu8.1) was installed on January 8 for me. The [changelog]("https://launchpad.net/ubuntu/+source/samba/2:3.5.4~dfsg-1ubuntu8.2") does indeed say the "bug" was fixed (YAY!), and I can now view my share with Windows Live Essentials 2011 installed. This has been mildly bothering me for a few months now, so I'm quite pleased.

Wow, the fix was put in the repositories a week after I started this thread, and the bug was reported and fixed 5.5 months ago. What timing.

Nautilus worked for me when I tried it, and I've rebooted my Ubuntu machine a few times since January 8. RickAN, have you tried restarting Nautilus ([FONT="Courier New"]nautilus -q[/FONT]) or Ubuntu?

---

### Post by RickAN on 2011-01-22
Hi,

Turns out it was my bad. Normally my Win7 machine is connected via wireless only. However - I was going to do some downloading so I plugged in the wired connection I have sitting here in case I screw up the wireless settings on the router. Well, having the Win7 machine on the network with 2 IP addresses was fine for it - but the non-windows machines weren't happy about it at all. I think it was because Windows would use the wired connection BUT the DNS server would return the wireless IP address on a lookup.

I discovered it tonight while trouble shooting - I turned off the wireless connection on Win7 and suddenly Ubuntu was saying machine not reachable. Hum, NSLOOKUP confirmed that the DNS server (an att UVerse router) was returning the IP associated with the wireless connection and not the IP for the wired connection that was still active. Turned on wireless, unplugged the wired connection and everything started working.

Anybody know if changing the NAME RESOLVE ORDER Samba parameter would help in this situation?

---

### Post by RickAN on 2011-01-22
Slight update:

I ran across an article tonight from Microsoft support - it's a tad old - but it was saying that a multi-homed host cannot be a Master Browser. Oops - my Win7 machine was in fact the master browser.

I must be getting senile in my old age - I used to know that.

---

### Post by ycherem on 2011-02-16
Did the trick for me, many thanks!

---

### Post by zeddock on 2011-06-13
No joy here!

Windows 7 64 bit trying to share with Ubuntu 11.04

Any other helps?

Thanx!
Zeddock

EDIT.............
Wait a second...
Upon reboot either this:
> Just to clarify, you just need to add the line:

client use spnego = no

to /etc/samba/smb.conf

or this:

> I figured I'd help out here.

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

Is an easy tutorial about how to fstab. When I did this I had trouble with fstab recognizing the computername rather than just the IP. The problem was resolved by adding "wins" to the /etc/nsswitch.conf like so:

Code:
hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4


.....ended up working for me.

---

