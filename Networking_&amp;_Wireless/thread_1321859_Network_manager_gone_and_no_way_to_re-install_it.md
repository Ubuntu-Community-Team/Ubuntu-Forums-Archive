---
title: "Network manager gone and no way to re-install it"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by BoomSchtick on 2009-11-10
I was having problems getting my Linksys WPC300N working on my laptop. I finally got it to work after installing Wicd. Life was grand until I went to use my Sprint (Sierra Wireless) aircard. Wicd does not support those devices so I uninstalled it to go back to Network Manager. Guess what... Wicd uninstalled network manager so now I can't connect to my aircard or to a wired connection.
 
It was at this moment that I felt the dependency of the internet in my life. Apt-get does not work because I have no internet connection.
 
How the heck to I get back to network manager without being able to connect to a blasted network?
 
I saw [this]("http://linuxd.wordpress.com/2009/02/09/installing-network-manager-manually-offline/") article, but it's not as simple as getting those four packages due to dependencies. 
 
I'm on a fresh Karmic install.
 
Thanks folks!

---

### Post by Hevydani on 2009-11-10
Go to Applications - 
Ubuntu Software Center -
 Type "Network Manager" into the search field

Place your Ubuntu Karmic disc into your drive and install the Applet.

Had to do it about half hour ago under exact same circumstances ;)


EDIT: Assuming you have a Karmic CD.........XD

---

### Post by bkratz on 2009-11-10
> **BoomSchtick said:**
> I was having problems getting my Linksys WPC300N working on my laptop. I finally got it to work after installing Wicd. Life was grand until I went to use my Sprint (Sierra Wireless) aircard. Wicd does not support those devices so I uninstalled it to go back to Network Manager. Guess what... Wicd uninstalled network manager so now I can't connect to my aircard or to a wired connection.
 
It was at this moment that I felt the dependency of the internet in my life. Apt-get does not work because I have no internet connection.
 
How the heck to I get back to network manager without being able to connect to a blasted network?
 
I saw [this]("http://linuxd.wordpress.com/2009/02/09/installing-network-manager-manually-offline/") article, but it's not as simple as getting those four packages due to dependencies. 
 
I'm on a fresh Karmic install.
 
Thanks folks!




here is what received about the same issue from someone who is pretty sharp.


[http://ubuntuforums.org/showpost.php?p=8258095&postcount=571](http://ubuntuforums.org/showpost.php?p=8258095&postcount=571)

---

### Post by dvirdc on 2009-11-10
well you can connect your eth cable and manually config eth0:

ifconfig eth0 <ip_address> netmask <netmask>

and add default gw:

route add default gw <ip_address> eth0

goodluck :)

---

### Post by BoomSchtick on 2009-11-10
> **Hevydani said:**
> Go to Applications - 
Ubuntu Software Center -
Type "Network Manager" into the search field
 
Place your Ubuntu Karmic disc into your drive and install the Applet.
 
Had to do it about half hour ago under exact same circumstances ;)
 
 
EDIT: Assuming you have a Karmic CD.........XD
 
 
I had tried that, but it never worked, so I figured I had to be online. I have the Karmic CD in and when I try to install that package, it still tries to go out to the web. It does not even spin the CD up... :shrug:

---

### Post by BoomSchtick on 2009-11-10
> **bkratz said:**
> here is what received about the same issue from someone who is pretty sharp.
 
 
[http://ubuntuforums.org/showpost.php?p=8258095&postcount=571](http://ubuntuforums.org/showpost.php?p=8258095&postcount=571)
 
 
It's strange... I had downloaded those packages and tried to install them but it always errored out.  Upon reading that I tried it in what would appear to the be correct order and it's working now...
 
Go figure...
 
Thanks for the responses!

---

