---
title: "Ubuntu 10.04 shortcomings: Windows networking."
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by Coder68 on 2010-08-21
I am running 10.04 and am unable to browse the network.  I can connect via smb://IPaddress to a WINDOWS box. But if I click on network and then  click on workgroup I get an error "Failed to retrieve the share list from server"

I was told to install samba but right after doing this, and making no changes, I could not even get the network to open the window, let alone see anything in it. It completely broke networking.  I purged Samba and was back where I started. I reinstalled and followed several samba how to's but the results were the same or worse. I am now at a purged state.

I do not want to have a share on my Ubuntu laptop, so it would seem to me that I do NOT need samba.  Is that a correct statement?

I do not want to have to type the address in every time I go to use a share! I have added bookmarks and will see if they work after a reboot, but I do not always know the IP of my shares, nor do I want dozen bookmarks. 

How do I fix this?

Coder68

---

### Post by Iowan on 2010-08-22
From Code of Conduct:> Please use color and font properties for highlighting portions of your text, and not for all of the text in your post.

---

### Post by uidb4056 on 2010-08-22
> **Coder68 said:**
> I am running 10.04 and am unable to browse the network.  I can connect via smb://IPaddress to a WINDOWS box. But if I click on network and then  click on workgroup I get an error "Failed to retrieve the share list from server"

I was told to install samba but right after doing this, and making no changes, I could not even get the network to open the window, let alone see anything in it. It completely broke networking.  I purged Samba and was back where I started. I reinstalled and followed several samba how to's but the results were the same or worse. I am now at a purged state.

I do not want to have a share on my Ubuntu laptop, so it would seem to me that I do NOT need samba.  Is that a correct statement?

I do not want to have to type the address in every time I go to use a share! I have added bookmarks and will see if they work after a reboot, but I do not always know the IP of my shares, nor do I want dozen bookmarks. 

How do I fix this?

Coder68

If you have installed Samba, go to System Menu - Administration -Samba  (or run in terminal gksu system-config-samba ) then go to Preferences  Menu and set the work-group the same as you have in your windows. Then  you should be able to browse your windows shares from my computer applet.

---

### Post by noelvh on 2010-08-22
Hi I feel your pain. I have compiled a doc/pdf I use. Now I have put this together from many different posts I have found. The PDF is a how to I follow. Then there is a copy of my Samba config file. There is the words CHANGE ME in it change it to some thing you like. 

I have saved this file in my UberNotes web site for the last year or so, and use it every time I setup a new pc.

I hope it helps you.

PS I get errors when connecting but I still connect, just give it a chance to connect and not keep clicking.

Noel

---

### Post by Coder68 on 2010-08-22
@Iowan

The font on my PC is super tiny and my old eyes cant read it. I just increased the size a bit.  It still looks like plain font to me, and not even bigger after I posted it.

Sorry.

@uidb4056

I did go to Samba and set it up with my workgroup name. Not only could I not see anything, when I went to places/network and clicked on it, the window would NOT open.  I had to purge samaba to get it to open the window again.

@noelvh

Thanks, I will check it out.

Coder68

---

