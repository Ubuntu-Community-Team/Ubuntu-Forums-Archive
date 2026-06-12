---
title: "WDTV Live Streaming Media Player and Linux (ubuntu) based NFS server"
date: 2011-11-18
forum: Multimedia Software
---

### Post by xcal8bur on 2011-11-18
So far my testing with the WDTV Live SMP has shown that NFS is superior to Samba, at least for wireless. I am able to stream 8-9GB .MKV 1080p DTS files without issue as long as I have a strong wireless N signal. I was able to setup windows XP with services for unix and create functional NFS shares off of my XP box. But now I am attempting to create a more permanent Linux(ubuntu) based NFS server but I've come accross a problem; the ip address of the Linux box is displayed, I can even log in and see the folders and files shared by ubuntu's NFSV4 or NFSV3 , but when I press play on the file, the first time after a reboot of the WDTV, I get the timer bar then a black screen, and each subsequent attempt to play the file, there is no timer bar and just the circular arrow spinning and of course after a long time nothing happens. In addition the WDTV Live SMP can no longer play files that it could before I attempted to play the Linux NFS shared file, that is until I power cycle the WDTV Live SMP.
 
I have searched google and these forums and have not found anyone who has successfully created a Linux based NFS server for the WDTV Live Streaming Media Player on stock firmware (I hope I'm wrong about this). Any info anyone has on how to do this would be very much appreciated. Or even any info regarding how to setup stable NFS shares with ubuntu would also be welcome.

---

### Post by xcal8bur on 2011-11-19
anybody have any ideas?

---

### Post by xcal8bur on 2011-11-21
You know it's the strangest thing, I finally managed to get Linux(ubuntu) serving functional NFS shares to the WDTV Live Streaming Media player, and Linux(ubuntu) is doing a worse job than Windows XP with services for Unix installed. The playback is nearly perfect on the XP machine, while on the Linux machine playback is choppy during many scenes sharing the same test files. In addition the Linux(ubuntu) machine is running on a Core i7 2.8 Ghz, Gigabit ethernet, and Raid 5. While the meager little Windows XP box has an Athlon XP 3.2 Ghz, 100 Mbps ethernet, and a normal hardrive. 
 
So does any one have any idea why this is happening?
 
does anyone know how to optimize a Linux NFS share?
 
P.s. what's even stranger than that is that when I connect the WDTV Live Streaming Media Player with a Cat 5e\Ethernet patch cord the Linux box performs even worse, so badly in fact that the Movie becomes unwatchable.

---

### Post by SeijiSensei on 2011-11-21
What transport protocol are you using on the NFS server, TCP or UDP?  The latter is the norm and is typically faster because there are no upstream acknowlegement packets being sent. However it's possible to use TCP for NFS services, but I wouldn't recommend it for media streaming.

I have no problem streaming 720p media over NFS with Linux servers and clients.  The client has a wifi connection to the network; the server is wired to the router.

If you can set up a wired ethernet connection between both devices, give that a try.  At least we'll have a handle on where the bottlenecks might be.

---

### Post by xcal8bur on 2011-11-22
Thank you so much for resonding SeijiSensei. Can you tell me where I can find the TCP, UDP setting to alter the NFS settings? also if you look at my first post I wrote that the performance gets even worse when I use a patch cable to connect the client, it's really strange, I think it may even be the patch cable. 
 
By the way why can't you stream 1080p?
 
P.s. it would be great if you could tell me what settings are best in the file /etc/exports
 
(ie., rw,fsid=0,insecure,no_subtree_check,async,sync,nohide,etc.,etc.)

---

### Post by SeijiSensei on 2011-11-22
You probably want to browse the [NFS HOWTO](http://nfs.sourceforge.net/nfs-howto/).

My server has async and insecure enabled, along with no_root_squash since my client mounts the share as root.

Unless you specified TCP specifically your server is almost certainly using UDP.

I'm not saying I can't stream 1080p; I just don't have much content at that resolution.  Remember, though, that 1080p consumes 2.25 times as much bandwidth as 720p  (=1920*1080/(1280*720)), and even when displayed on my 40" Sony Bravia I don't discern enough improvement in quality to justify the higher resolution.

The fact that you're having problems with a wired connection suggests there might be something more problematic going on with your network infrastructure.  When you connect the device over Ethernet, are you using a shared switch?  Have you tried connecting the server to a different port on the switch?  I presume the switch is at least 100 Mbit, yes?  Perhaps it's just a bad cable from the server to the switch or router.  Cat5 performance is very susceptible to kinks and bends in the wire itself.

With Linux you can specify a blocksize for transfers on the client side.  I generally use 32768 for both reads and writes.  I don't see a blocksize parameter for the server, though.  Perhaps there are settings in the WDTV device that might let you tune the performance of NFS?

---

### Post by xcal8bur on 2011-11-22
Thanks for all the extra info SeijiSensei, your right on TV's smaller than 50 inches 1080p is kind of a waste from more than 7 feet away anyway. But I have two 58 TV's that I need to feed. I'm definitely going to check out that HOW TO, I've looked at dozens already. And it's a router with gigabit ports, I will install cat6 solid soon and see if the cabling is the problem.
 
What do you mean by shared switch? are'nt they all shared.
 
can you specify the client block size through the server? or are you saying if the client was another Linux box THEN you could specify the client block size.
because I don't think there are any settings on the WDTV Live SMP itself to do this, I will make sure though

---

### Post by SeijiSensei on 2011-11-22
> **xcal8bur said:**
> What do you mean by shared switch? are'nt they all shared.

Yes.  Sorry if that was confusing.

> are you saying if the client was another Linux box THEN you could specify the client block size.

Yes.  I mentioned it only to suggest that if an equivalent setting existed on the WDTV device you could try changing it.

---

### Post by xcal8bur on 2011-11-25
It turns out the biggest contibutor to the descrepancy in performance between my Linux box and Windows XP box, when it comes to serving up NFS, was flaky Gigabit ports on my router. When I installed a new router (ASUS RT-N56U) and set up my SAGEMCOM 2864 in bridge mode most of the problems went away. and Linux was able to serve NFS just as fast as windows to the WDTV Live Streaming Media Player. also the SAGEMCOM 2864 's wireless was just as flaky, giving me only two bars in the basement while the RT-N56U gives me full strength wireless everywhere in the house including the basement.
 
Thank you so much for your suggestions SeijiSensei. They helped me get a handle on the problem much quicker than if you had'nt given them.
 
P.S> how do I change this thread to [SOLVED]?
 
Edit: wait, it seems I still can't declare this solved, because, I believe the cat5e I'm using is still causing a problem, I will switch to Belden cat6 and see if that clears away the problem totally, before I declare it solved.

---

### Post by gordintoronto on 2011-11-25
At the top of the page, Thread Tools.

---

### Post by thevolumnus on 2011-12-14
I had Hanewin up and running all evening, but when I shutdown the machine, it would not restart. I tried everything to get it restarted, but I was unsuccessful. I then tried for two hours to get Truegrid NFS server running on my Windows 7 64bit Laptop to no avail. So...I'm currently without an NFS server and having to use Samba. This little box is a source of frustration. I would never have bought it if I could have foreseen the amount of time I would waste trying to make it work right. I cannot understand why it will not support 5ghz wifi. I mean...I have this tricked out router with a selectable setting to stabilize bandwidth for streaming HD video among network devices. However, the feature has never been used because the SMP doesn't support 5GHZ. Also, why even have the option to stream from NFS when you can spend half your life looking for an NFS server that works and never find one and if you find one like hanewin you'll spend a year getting it dialed in, and then  it stops working...ughhhhh!
> **xcal8bur said:**
> So far my testing with the WDTV Live SMP has shown that NFS is superior to Samba, at least for wireless. I am able to stream 8-9GB .MKV 1080p DTS files without issue as long as I have a strong wireless N signal. I was able to setup windows XP with services for unix and create functional NFS shares off of my XP box. But now I am attempting to create a more permanent Linux(ubuntu) based NFS server but I've come accross a problem; the ip address of the Linux box is displayed, I can even log in and see the folders and files shared by ubuntu's NFSV4 or NFSV3 , but when I press play on the file, the first time after a reboot of the WDTV, I get the timer bar then a black screen, and each subsequent attempt to play the file, there is no timer bar and just the circular arrow spinning and of course after a long time nothing happens. In addition the WDTV Live SMP can no longer play files that it could before I attempted to play the Linux NFS shared file, that is until I power cycle the WDTV Live SMP.
 
I have searched google and these forums and have not found anyone who has successfully created a Linux based NFS server for the WDTV Live Streaming Media Player on stock firmware (I hope I'm wrong about this). Any info anyone has on how to do this would be very much appreciated. Or even any info regarding how to setup stable NFS shares with ubuntu would also be welcome.

---

