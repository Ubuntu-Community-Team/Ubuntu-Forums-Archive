---
title: "simple ethernet link between 2 computers running Jaunty"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by paddymurphy on 2009-10-14
Hello

Can anyone help a newbie with what is probably a simple thing?

I have two computers, both running Ubuntu 9.04.

I want to link them with an ethernet cable simply so that I can move files between them.

Can anyone tell me what to do after plugging the cable in?

Many thanks indeed!:)

---

### Post by trundlenut on 2009-10-14
Depending on your network cards you will likely need a cross over cable to be able connect them or they both end up sending data down the same wire.

---

### Post by oldfred on 2009-10-14
Do you have a hub or router? Otherwise you need a special "crossover" ethernet cable that makes one set of wires the "in" at one end and "out" at the other. A simple hub is often cheaper than the special cable unless you know how to make your own.

Generally set up Samba and turn sharing on for what ever partitions you want to share.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

This link also has links to more Samba info.

---

### Post by paddymurphy on 2009-10-14
Many thanks indeed for that. 

I had a vague idea that a different type of cable is required. I've got a whole box full of ethernet cables, but I'm not sure how to tell which are of the crossover type. Is there anything obvious marked on them to tell them apart?

Many thanks again.

---

### Post by paddymurphy on 2009-10-14
Many thanks for that - I've already (in a reply to another helpful user) my next question - how do I know if a lead is the right type?

Many thanks again.

---

### Post by oldfred on 2009-10-14
Cables are almost never the crossover type. Before I bought my hub, then my router I had to make my own.

You can get a small 4 port hub pretty cheap.
[http://www.google.com/products/catalog?hl=en&source=hp&q=ethernet+hub&um=1&ie=UTF-8&cid=8071494353598052289&ei=VGPWStirOpDSNcXKtN0D&sa=X&oi=product_catalog_result&ct=result&resnum=1&ved=0CBcQ8wIwAA#ps-sellers](http://www.google.com/products/catalog?hl=en&source=hp&q=ethernet+hub&um=1&ie=UTF-8&cid=8071494353598052289&ei=VGPWStirOpDSNcXKtN0D&sa=X&oi=product_catalog_result&ct=result&resnum=1&ved=0CBcQ8wIwAA#ps-sellers)

I have seen them on sale for even less.

---

### Post by baggins on 2009-10-14
> **oldfred said:**
> 
Generally set up Samba and turn sharing on for what ever partitions you want to share.
Or just install openssl-server on one machine, and sshfs on the other (or install both on both machines). The first time you must make an empty dir  on the machine with sshfs installed (I always use /home/$USER/mntpt). 
Then connecting is as easy as executing:
```
sshfs -o cache=no -o reconnect -o follow_symlinks remoteUser@remoteIP:/folder/to/be/shared $HOME/mntpt
```
To stop sharing the folder just run the command
```
fusermount -u $HOME/mntpt
```
No further configuration is required, on the local machine there will be a folder "mntpt" in your home dir that contains what ever you requested from the remote machine.

If you need the folder all the time, you just add the command as a startup application (don't bother unmounting that will happen automatically when you log out)

Personally I only use samba if I need to share data with a windows machine, otherwise it's just too much work setting it up right :)
And of course the fact that sshfs is encrypted makes my paranoia demons very happy, when you add my not so secure network uplink into the mix \\:D/

> **paddymurphy said:**
> Many thanks for that - I've already (in a reply to another helpful user) my next question - how do I know if a lead is the right type?

Many thanks again.
Look at the flat side of the plug at both ends of the cable. You will see 8 colour coded wires inside the plug (some of the wires will likely be white with a coloured stripe). A common colouring is from right to left white/orange, orange, white/green, blue, white/blue, green, white/brown, brown.
 If both ends of the plug are identical then the cable is not a crossover cable, otherwise it might be :)
But by a hub, switch or router (with built in switch), that way you can also use your internet connection on both machines

-- Jon

---

### Post by baggins on 2009-10-14
<offtopic>
> **oldfred said:**
> 
You can get a small 4 port hub pretty cheap.
[http://www.google.com/products/catalog?hl=en&source=hp&q=ethernet+hub&um=1&ie=UTF-8&cid=8071494353598052289&ei=VGPWStirOpDSNcXKtN0D&sa=X&oi=product_catalog_result&ct=result&resnum=1&ved=0CBcQ8wIwAA#ps-sellers](http://www.google.com/products/catalog?hl=en&source=hp&q=ethernet+hub&um=1&ie=UTF-8&cid=8071494353598052289&ei=VGPWStirOpDSNcXKtN0D&sa=X&oi=product_catalog_result&ct=result&resnum=1&ved=0CBcQ8wIwAA#ps-sellers)
Actually that's a usb hub, the ethernet part is just a normal cable that can be rolled up into a transport box. The title on google is pretty misleeding, wonder how common that is?
</offtopic>

---

### Post by D Thunderbird on 2009-10-14
If you hold the connectors next to each other and the same color wires go to the same pins then it is a straight not a cross over.

---

### Post by trundlenut on 2009-10-15
Crossover cables normally have "cross over" or similar written on them!

---

### Post by paddymurphy on 2009-10-15
Many thanks for that - I'll review my options!
Learning all the time!

---

### Post by paddymurphy on 2009-10-15
Wow - very full and helpful answer. Many thanks indeed!

---

### Post by paddymurphy on 2009-10-15
aha! I suppose I should have guessed that - but this is how we learn!

Many thanks indeed.

---

