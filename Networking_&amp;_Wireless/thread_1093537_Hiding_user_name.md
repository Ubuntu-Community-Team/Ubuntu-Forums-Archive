---
title: "Hiding user name"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by mrl777 on 2009-03-11
Hello,

I'm using a free neighborhood wireless connection.  How would I go about hiding my machine/user name when connected to the network?  I don't mind the mac address showing up (that's unavoidable), but not my system user name or any other labels.

Also, I reinstalled Ubuntu and I noticed something has change on the wireless connection I use.  It used to have a drop-down side menue for connecting to the neighborhood wireless network (two subnetworks?), but now it's just a directly accessible menu item like all the rest of the available wireless networks.  What does this mean?

I used to have to go to the left sub-menu and I would see two available networks on one connection, now it's just one item to connect to the network.  Very strange.

---

### Post by jonobr on 2009-03-11
If I were a complete cynic I would think you are actually using somebody else's wifi and wanting to hide yourself from them knowing who you are,

But then again, that's just me being cynical of course.

---

### Post by kidux on 2009-03-11
> **jonobr said:**
> If I were a complete cynic I would think you are actually using somebody else's wifi and wanting to hide yourself from them knowing who you are,

But then again, that's just me being cynical of course.
Indeed. :popcorn:

---

### Post by mrl777 on 2009-03-11
> **jonobr said:**
> If I were a complete cynic I would think you are actually using somebody else's wifi and wanting to hide yourself from them knowing who you are,

But then again, that's just me being cynical of course.

No -- it's a neighborhood network connection.  It's been up for some time now and it is totally unsecured.  If they didn't want people on it then they would most definitely secure it (its' easy to do).  However, they do tend to kick people off of it if its get too busy. If I were hacking into people's networks I would not be so stupid as to post the type of request I posted.  I would have worded it in a totally different way to hide my intent.

I just don't like the idea of others on the network being able to see that information.

---

### Post by jonobr on 2009-03-11
Im not sure who you want to hide your information from , is the people who own the equipment? The government? etc
Unless you doing stuff over ssh or to secure websites, you really need to consider that what you do is open.
If you want some degree of privacy through the AP
then use something like openvpn [here]("http://http://openvpn.net/")

create a vpn through the access point to a vpn terminator.The cost for doing this is that you get adds fed to you while using the vpn connection.
Your information is in a secure tunnel which is decoded at the provider end.

lastly , 
Using somebodies unsecured wireless network is not really hacking

---

### Post by solitaire on 2009-03-11
IANAL!
But in legal terms think it's still illegal to access it even though it's not secured. (I.E. Just because the house door is open does not give you the right to walk in and take the TV.)

---

### Post by mrl777 on 2009-03-11
> **solitaire said:**
> IANAL!
But in legal terms think it's still illegal to access it even though it's not secured. (I.E. Just because the house door is open does not give you the right to walk in and take the TV.)

Not quite the same thing.  There are issues of offer and acceptance.  If it were the intent of provider to not want people on it then they would simply secure it, whereas for a home it would depend on the circumstances leading to the open door.  Networks and buildings are not the same.

In law, there is a maxim that says "He who does not forbid what he can then consents.", and another maxim that says "He who consents cannot claim an injury."  So, should they forbid access to the network by securing it and if I should hack into it then I would be trespassing.  The act of securing the network is like a do not enter sign.  But if you do not forbid access to it by leaving it wide open then it an invitation, as there is no way for anyone to know if they are not truly invited.  You cannot prove something called "mens ray", which is to say "A guilty mind." and this is necessary in law to secure a criminal conviction.

If you constantly left your door wide open to your home and you saw definite signs of entry and usage of your home then you have no case for trespass unless you report it.... or unless you put up a sign that said DO NOT ENTER,  The people that were in your home were merely taking you up on your repeated offer.  It just depends on the circumstances.  For homes, they are generally not open to the public, as they are, by custom, private buildings.  But networks are different because there is often no way to tell if a network is totally private unless it is secured.  It's not as if there's a sign posted telling everyone that only certain people can enter this unsecured network.  In this case, as I said, that "sign" would be in the form of a secured connection.

---

