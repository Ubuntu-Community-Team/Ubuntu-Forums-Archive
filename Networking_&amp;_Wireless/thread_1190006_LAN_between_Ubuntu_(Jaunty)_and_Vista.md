---
title: "LAN between Ubuntu (Jaunty) and Vista"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by autocrat25 on 2009-06-17
I'm a quite new to linux and I'm trying to setup a LAN connection between my ubuntu laptop and my friend's vista laptop. My friend's laptop gets detected on mine but I'm unable to open the contents also my laptop isn't getting detected on his. Any solutions to this?

Thanks in advance.

---

### Post by coffeecat on 2009-06-17
I presume you mean by means of Windows shares.

First. If you've made the mistake of installing Firestarter, **uninstall** it.

Now...

> **autocrat25 said:**
> my laptop isn't getting detected on his.

You need to set up a Windows share in Ubuntu. However, Jaunty doesn't come with the smb client by default, but it's easy to add. Create a folder in your home desktop for sharing purposes. Call it what you want, but this will be the name of the share. Right click on it and select 'sharing options'. In the little Window that opens, tick the 'share this folder' box. You will be told that something needs to be installed - just follow the prompts. When this is done, log out and login again. Right-click on the folder again and set up the share. This should now be visible in Vista.

> **autocrat25 said:**
> My friend's laptop gets detected on mine but I'm unable to open the contents

This is a common problem and rather unpredictable. I installed Jaunty on four machines. I was able to browse Windows shares no problem at all on one out of the box, but on the other three I had to do one or more of the fixes described here:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Don't be intimidated by the instructions. Just take it easy. The most important three are ensuring that your Vista workgroup is "WORKGROUP" or editing smb.conf so that Ubuntu is in the same workgroup as Vista. Second - edit smb.conf so that the leading ; is removed from the line:

```
 name resolve order = lmhosts host wins bcast 
```Third - edit nsswitch.conf as instructed, adding "wins". Also install winbind. You can do that through Synaptic if you prefer.

Then you should be good to go. By this means I have all my Jaunty and Windows machines talking to each other and to my network fileserver.

---

### Post by autocrat25 on 2009-06-19
> **coffeecat said:**
> I presume you mean by means of Windows shares.

First. If you've made the mistake of installing Firestarter, **uninstall** it.

Now...



You need to set up a Windows share in Ubuntu. However, Jaunty doesn't come with the smb client by default, but it's easy to add. Create a folder in your home desktop for sharing purposes. Call it what you want, but this will be the name of the share. Right click on it and select 'sharing options'. In the little Window that opens, tick the 'share this folder' box. You will be told that something needs to be installed - just follow the prompts. When this is done, log out and login again. Right-click on the folder again and set up the share. This should now be visible in Vista.



This is a common problem and rather unpredictable. I installed Jaunty on four machines. I was able to browse Windows shares no problem at all on one out of the box, but on the other three I had to do one or more of the fixes described here:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Don't be intimidated by the instructions. Just take it easy. The most important three are ensuring that your Vista workgroup is "WORKGROUP" or editing smb.conf so that Ubuntu is in the same workgroup as Vista. Second - edit smb.conf so that the leading ; is removed from the line:

```
 name resolve order = lmhosts host wins bcast 
```Third - edit nsswitch.conf as instructed, adding "wins". Also install winbind. You can do that through Synaptic if you prefer.

Then you should be good to go. By this means I have all my Jaunty and Windows machines talking to each other and to my network fileserver.
Thanks coffeecat, that helped alot. But I encountered another problem, everything was working fine and after a while the connection was lost. This kept happening frequently, any solutions for this too?

---

### Post by coffeecat on 2009-06-19
> **autocrat25 said:**
> Thanks coffeecat, that helped alot. But I encountered another problem, everything was working fine and after a while the connection was lost. This kept happening frequently, any solutions for this too?

Hmm. I don't know. I used to have a similar problem when my fileserver was a cheap n' nasty enclosure for a hard drive. While copying large files (or sometimes small ones), the copy would stall and then error out. But the problem was in the cheap n' nasty fileserver. I can browse shares and copy files quite OK now between Ubuntu, Vista, MacOS and a new Western Digital fileserver.

When you say the connection is lost, does the Ubuntu share disappear from Vista or the Vista one from Ubuntu, or both? Or do you get stalling with file copying like I did? Have you checked your firewall settings on Vista? Network problems are often down to firewall issues, although I would have thought a firewall problem would prevent you connecting to a share in the first place. By the way, the reason I suggested uninstalling firestarter from Ubuntu (if you'd installed it) is that it can cause real problems. It's a nice GUI interface but clearly very buggy and best avoided. If you really need to configure firewall settings in Ubuntu you're better off with using the inbuilt ufw by installing the gufw GUI interface.

The only other thing I can think of is if there is a router problem. Was one of the machines losing its DHCP lease? When whichever share disappeared, could both machines still access the internet?

---

### Post by dmizer on 2009-06-19
> **autocrat25 said:**
> Thanks coffeecat, that helped alot. But I encountered another problem, everything was working fine and after a while the connection was lost. This kept happening frequently, any solutions for this too?

Are you connecting wirelessly? If so, you may want to try a different networking manager like wicd instead of the default "network-manager".

Either way, please post the output of:
```
lshw -C network
```

---

### Post by autocrat25 on 2009-06-20
Thanks again for your reply, I figured out the problem. It was actually a very silly and minor fault. The wire on my friend's laptop port kept coming off. :P But then again thanks and sorry for all that trouble.

---

