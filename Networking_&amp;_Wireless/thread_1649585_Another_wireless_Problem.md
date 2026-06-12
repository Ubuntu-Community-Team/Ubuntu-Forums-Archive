---
title: "Another wireless Problem"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by clintgreen on 2010-12-20
New to forum and quite new to any linux distro, have played  around a little with older Ubuntus, having spare desktop I thought it was time to see how things are developing with the latest release.   10.10, downloaded and cd made.  

Installed without a hitch, picked up all the hardware even my Edimax 712g nic. entered wireless network details and was off.  Enjoying the new look and feel of the OS  surfing, mailing and connecting to my win 7 laptop for my music shares.    We then had visitors round so shut down, and went back to it this morning, only to find that a couple of things had changed.

(1) no matter what I do (Followed several different suggestions found on here) and no matter how many times I check all the details, It will not connect, to the router just carries on  seemingly without end trying; only broken by the requests for the security key of the router.

(2)  the keyring password is not recognised.  

I thought I may have done something I didn't realise, so I simply did a reinstall, everything exactly the same, and just replicate the problem I perfromed a restart; ending up with exactly the same result.

What a shame, I would love to be able to use it wirelessly, so hopefully someone can come up with an answer for me, I can go wired using a "HomePlug" and will if I have to as I quite simply like this release

---

### Post by grahammechanical on 2010-12-20
When network manager repeatedly asks for authentication of a wireless connection it is because the security key is the wrong one. Or, you are trying to connect to the wrong wireless network. If you are set up to automatically login then you will be required to enter a password to make a wireless connection. It is possible to get confused and use the login password to authenticate a wireless connection. If that happens then network manager will remember that password. It will no longer use the security password. I have been caught out by this.

Right click the network icon and select Edit Connections. Make sure the correct security pass phrase or key is in place and set the wireless connection to Automatically connect and to be available to all users.

Regards.

---

### Post by clintgreen on 2010-12-21
;)  Yea thought of that,  and made sure that the passwords were ok,  in fact I have them on a card in front of me,  I virtually always log down the way I do things when working on something new. (anal I know, but it helps when backtracking)

  I was going to try and use the same password for just about everything.

The password definately changed on the keyring, I deleted that, saved a new one and that changed upon reboot  3 times.


  The ssid and network password are set by Sky in their pre configured router an CD.

stumped for now, am going to move the pc nearer a wall plus so I can use "Homeplug" for a wired connection, while I try and get this sorted out.

cheers for replying

Seasons Greetings

---

