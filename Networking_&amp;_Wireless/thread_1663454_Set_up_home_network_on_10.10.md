---
title: "Set up home network on 10.10?"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by savaan on 2011-01-09
I'm having some difficulty figuring out how to network 2 Maverick computers. My wife and I are on a router together and I simply need to share printers and have the ability to move files back and forth. 
I've installed samba on both, and she can see but not enter my computer....I can't even see hers or the network.

Anyone know where I should start?

---

### Post by Mistiq Dragon on 2011-01-09
I'm pretty much working on the same situation myself.  I will tell you that once you get the right procedure, you'll be shocked at how easy it is, but I haven't quiet figured out how to do it myself.

I know that from my experience, Samba hasn't been that great for me when it comes to networking two Maverick Computers, at first I avoided SSH because I thought it was complicated but tried it and it looks a lot easier than I expected and it may provide what you and I both need.
[Read This Link.  ]("http://www.jonathanmoeller.com/screed/?p=891")
 
It may look complicated, but it's one command and then you edit a txt file, no big deal.

Do that on both computers and you can access each other's computer with no problem.  


What my problem has been is the fact that it's hard to find Straightforward advice about things like this, either it's so basic it doesn't help or they assume you know things that you don't.   

I think that if you can Ssh into each other's computer with no problems, that should put you on the path you need to be on.

This goes into a lot more detail about Ssh and the things you can do with it.[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)


Hopefully, you're able to set up the Ssh and then find information to help you  with that printer.
I feel that this is the right way to go because Samba has always given me a lot of problems when it comes to networking two Ubuntu computers.

---

### Post by PatchesTheCaveman on 2011-01-10
Try using NFS to share files between the two computers.  NFS is usually the best solution for sharing files between Linux computers.  SSH would work, but it acts more like FTP than Windows file sharing, which might not be what you want.

There's a HOWTO here:  [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

To get printing working, you should be able to go to System > Administration > Printing on the other computer and add the printer on the first.

---

