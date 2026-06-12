---
title: "Two Ubuntu Machines via Wireless"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by Spartachris on 2009-08-10
Help! I have been banging my head against the keyboard for days now trying to get two Ubuntu machines to share files. I know there are hundreds of posts and tutorials, but I cannot find things that apply and/or work for me. Part of the problem is my own ignorance. Help would be great!

Here's my situation:

I have the Cable Modem connected to a wireless router. That Network is called "FAMILY".

I have a desktop running Jaunty "christopher-desktop" that connects wireless to "FAMILY". No problems with the internet.

I have a new notebook that runs Jaunty "christopher-laptop" and connects wirelessly to "FAMILY". No problem. Both connect to the internet fine.

I cannot get them to connect together.

What I want to do is to be able to access pictures and music off "christopher-desktop" from the laptop.

I've tried samba and who knows what else.

Using the laptop, when I use nautilus to click "Network" it shows "Windows Network." When I click that it shows "Workgroup". When I click that it returns an error: "Unable to mount location: Failed to retrieve share list from server."

I really appreciate any help that you can give.

Thanks!

---

### Post by arch0njw on 2009-08-11
To get the network to work, you'll need to get samba to work.

As a first check, have you tried this guide for getting Samba to work?

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by The Pinny Parlour on 2009-08-11
I'm am now having EXACTLY the same problem you have described.  

It is a little annoying and I would like to now how to correct it.

---

### Post by Spartachris on 2009-08-11
arch0njw--

Thanks for the reply. 

I can't get those instructions to work. I followed the steps for "Server" and "Client", installing samba on the desktop and smbfs on the laptop. I right clicked on the folders I want to share on the desktop and selected "Sharing options", selected share folder, gave it a share name and allowed guests. Then I went to the laptop and clicked "Network" then "Windows Network" and got the error "Unable to mount Location: Failed to retrieve share list from server." I got the same error when I clicked "Windows Network" on the laptop.

So I am stuck. I wish I knew more and appreciate your help!

---

### Post by The Pinny Parlour on 2009-08-11
Who would of thought networking two Ubuntu PC's would be so difficult. :(

---

### Post by Spartachris on 2009-08-14
I've done more searching and still can't figure out where to go from here. Anyone have any idea?

Thanks!

---

### Post by rtrdom on 2009-08-14
Have a look in /etc/hosts. Ensure the IP address of the computer to which you are trying to connect is identified. Otherwise, it may not know what to do . I know when
ever I want to talk to another of my computers over ssh, I must have the IP perhaps
because I'm on a secured, static IP address network.
Hope this works for you.

---

### Post by Spartachris on 2009-08-14
Thanks for the tip rtrdom!

I added the Desktop's IP to the /etc/hosts file and now when I click on Windows Network it shows "Workgroup"...but when I click on that, I get the "Unable to mount location: Failed to retrieve share list from server."

I checked out the router settings and the router sees the desktop and laptop and the wireless printer. I should have added that both systems can use the wireless printer as well.

---

### Post by Spartachris on 2009-08-15
After reading and obsessing about this more, I discovered that I the two machines could find each other via DAAP in Rhythmbox. All I needed to do was to give it the desktop's ISP and, lo: all my music.  

Which is cool...but also frustrating that Rhythmbox can find my laptop, but not Nautilus. Or Samba. Sigh.

So this leads me to believe that it's probably /etc/samba/smb.conf that is messed up somewhere, since it's not a firewall or wireless connection issue.

How do I figure out what's wrong from here?

Thanks.

---

### Post by lswb on 2009-08-15
I can't help with samba, but it is not needed for sharing files between ubuntu or linux/unix systems. Just install openssh-server on both machines. You may need to logout/login or perhaps reboot, then just go to Main Menu/Places/Connect to Server, select SSH as server type, fill in the fields, hit connect, and the remote system will be available on the Places menu or from the nautilus sidebar. If you prefer, you can install an ftp server and use ftp instead, but IMHO SSH is the easiest way to go.

If you use cli much you may want to also install the sshfs package. It allows you to mount a remote system or directory on remote system to a local directory, much like the mount command works for mounting local partitions.

Your router will normally not allow SSH traffic from the internet to hit your systems, so you don't have to worry about that unless you've enabled NAT on the router to do so. Most likely you will have no problems but if you have ever configured a firewall on either system to block SSH traffic you may need to change settings to allow SSH on the local (private) lan.

---

### Post by Iowan on 2009-08-15
[This]("http://ubuntuforums.org/showthread.php?t=1169149") How-To is for fixing Windows share problems, but since Samba is involved...

---

### Post by Spartachris on 2009-08-15
Lwsb: it worked! Awesome and thank you!

I used sshfs to mount the dir with music and it worked too! 

I am still concerned that Samba doesn't work. Loose ends, you know?

And my other peeve is that the laptop and my wife's laptop both dual-boot Vista. When we were both powered up this morning, it gave us shared folders with one simple click. I love Ubuntu and would use it exclusively if not for work-related issues, but why can Vista get this to work effortlessly and not Ubuntu? Again, I think Ubuntu should rule the world, but it makes me sad when Vista does something so much better.

Thanks again for your help!!!

---

### Post by Spartachris on 2009-08-16
Iowan--That how-to worked!! I hadn't seen a few of the steps anywhere else--the step about nsswitch and the winbind, which I hadn't installed. Now it seems to be working, though I need to do some tweaking on the shares on the server-side (Desktop).

Again, thanks everyone for your help. I wish it were easier, since Ubuntu is supposed to "just work," but at least it does for me now.

---

