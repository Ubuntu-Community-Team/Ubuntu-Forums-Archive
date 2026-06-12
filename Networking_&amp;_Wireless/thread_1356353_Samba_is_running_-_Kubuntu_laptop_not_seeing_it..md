---
title: "Samba is running - Kubuntu laptop not seeing it."
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-12-16
I got Kubuntu on my desktop running Samba. In front of me I have a Mac laptop and a Kubuntu laptop.

The Mac can see and connect to my Samba share.
The Kubuntu can not see my Samba share.

I tried dolphin and konq. Nothing in either. What can I try with this?

---

### Post by sanderj on 2009-12-16
On which machine is the Samba share that can be seen? On the Mac, or on the Kubuntu, or on another machine?

On the Kubuntu machine, have you tried the CLI tools smbclient and nmblookup? You need to know that samba name of the machine you want to see. Example: on my LAN is a machine "athlon64" running Samba. From another machine, I can run the CLI tools:

nmblookup athlon64
smbclient -N -L athlon64

---

### Post by Iowan on 2009-12-16
[This]("http://ubuntuforums.org/showthread.php?t=1169149") How-To might help with some of the issues.

---

### Post by Roasted on 2009-12-21
Nope. No dice. I tried everything I could, however some of that didn't apply to me because I'm working with Kubuntu-to-Kubuntu and not Windows-to-*Buntu.

So in short, I have a Kubuntu desktop running Samba. The Mac laptop I'm on now can see it, access it, etc. Yet my Kubuntu laptop cannot see it no matter what I do.

This is really starting to drive me insane. What can I do? I have no problems accessing Windows shares at work, and that's on a domain while my smb.conf says I'm in a workgroup named "workgroup." Yet here at home I use the default workgroup for the network as simply "workgroup" and I STILL can't get anywhere....

---

### Post by Roasted on 2009-12-23
All right. This is really starting to piss me off.

Here I am on the Kubuntu laptop again. Hit my Samba share. Bam, fine.

Closed out of dolphin, did some stuff on firefox, and tried to go back to my Samba share. No shares found.

Awesome. Really? Just awesome.

Maybe I should also set up an NFS share so I can hit it from linux-to-linux with this laptop and my desktop. Can I have NFS and samba co-exist and even share out the same folder with samba AND nfs? Cause it's nice having samba since it plays nice with my windows laptop and mac laptop too...

---

### Post by Roasted on 2009-12-28
Bumpin till we get an answer. Any insight?

---

### Post by Roasted on 2009-12-29
So I went into the Ubuntu and Kubuntu IRC and found some people who offered some insight. It was recommended to me that no matter what you do, "browsing" with Samba can often suck, meaning to go through the network neighborhood and all of that crap.

Well, I'm here with SMB4k and Dolphin - both which were unable to find my shares. I was able to ping the storage server by name and by IP - yet Dolphin and SM4k didn't find anything when I scanned for network servers. So the one guy in the Ubuntu IRC said something about when he uses Nautilus, he ONLY uses the direct path aka - smb://storage/roasted/mystuff. So I opened Dolphin up and hit edit - view editable address bar - typed that in - BLAM. Worked.

Turned around and tried to browse the samba servers through the neighborhood... didn't work.

SO, while it kind of sucks that I can't view them through browsing, it doesn't matter because I just dragged the quick icon from my folder over anyway, so it's no big deal. I also tried this in Konqueror too, which worked fine.

So, question to you guys. Ubuntu and Kubuntu users alike - have you ever had any issues "browsing" samba servers like I did? My co worker here is using Ubuntu and had some weirdness at one point, but once she saved the link on the left side to just real quick - blam - on her folder, things were good. I'm hoping the same is true for the same thing I just did in Kubuntu.

Anymore insight?

---

### Post by travlemon on 2011-06-27
> **Iowan said:**
> [This]("http://ubuntuforums.org/showthread.php?t=1169149") How-To might help with some of the issues.

Hey, I know this is an old thread, but I'm having trouble finding another newer one that I wanted to respond to.  I wanted to shed maybe a little bit of light on this issue.

Since this is a very late post, I'm running Kubuntu 11.04, and Iowan's fix (referenced above) is the one I follow religiously to fix the browsing issues via Gnome desktops.

Now that I switched to Kbuntu and KDE, I figured that this fix would be no different...and it isn't...but KDE/Dolphin can trick you into thinking that Samba browsing is not working, when it might be working fine.  Just keep in mind that this is on Kubuntu 11.04, this is what my situation was like:

**_My version of the issue:_  **I open Dolphin, click on the Network link on the left hand side.  I click "Samba Shares", and it looks like it tries to load, but the window stays blank, as if the folder is empty.  I noticed that if you press CTRL + L, to view the location in the location bar, it says **smb:/** instead of the usual **smb://**.  I don't know if it makes a difference or not, but every other time I browse on other distributions, it says **smb://** in the location bar of the distribution's file browser.  If I manually type **smb://** in the location bar, it still redirects to **smb:/**.

I also noticed that if I manually typed the location of the desired network share (**smb://kitchen-pc** for example), it would display the shares no problem.  It also worked if i specified the workgroup (**smb://mshome** for example).  So I changed the **Samba Shares** shortcut to point to **smb://mshome** and it seems fine now.  If you need help, there are some instructions below.

_**My Fix (it's more of a workaround):**_ This should suffice nicely for you, if your network only has one workgroup.  Basically, all I did was open Dolphin up as root (via the **sudo dolphin** command in the terminal), and click on the Network link on the left hand side of the Dolphin window.  Then, right click "Samba Shares" and click properties.  In the *"Points To*" field, modify it so that it says **smb://mshome** (you can replace *mshome* with your own workgroup name), instead of **smb:/** and click OK.  

Close the root Dolphin window and open it with the normal current user's privileges, and click on the Network link on the left hand side of the Dolphin window again.  You may have to press F5 once just to refresh the window, then double click on **Samba Shares** and hopefully you'll get a pleasing result.

Hope this helps!

EDIT:  Ok, after writing all that, my Samba shares are magically working.  I'm not sure what changed.  The only thing I did, AFTER writing the above post, was try installing samba4 and winbind4.  I still got no results after rebooting.  I guess maybe the original Samba fix was actually effective, but for some reason the successful result was delayed?  In any case, my above instructions may still be of use to someone who just can't seem to get that "Samba Shares" link to work properly.

For those of you still having problems, here is a link to a video I made, of how to perform the Samba fix.  It shows me explaining it and doing it step by step, I cut out the steps of adding firewall exceptions, as it's never been a problem for me.  Also please note that you must install the package called **winbind** (you may ignore my above mentioning of samba4 and winbind4).  I forgot to show in the video that you must install **winbind**, but I did leave an annotation that says to install it.

[http://www.youtube.com/watch?v=lqETu4dWQrI](http://www.youtube.com/watch?v=lqETu4dWQrI)

---

