---
title: "Make wireless connection at reboot in Karmic?"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by wonk-o-matic on 2009-12-05
I have a wireless Karmic Koala box that I need to ssh into and that serves a website (local LAN, only).  There are unsecured routers in my neighborhood, and the users are (mostly) my children.  

1. Is there a way to make my wireless connection come up at reboot?  


2. I don't want users to be able to make any changes to the connection.  (There are unsecured routers in my neighborhood, and the users are my children.)  

3. I don't want users to have to authenticate to use the wireless LAN.  

I used to do all this with configuration files, but would like to be able to use the default Karmic tools.  Any ideas how to do this in Karmic?

---

### Post by chili555 on 2009-12-05
The default network tools, Network Manager, et al, allow users to select from many networks...by default. It seems to me that you are asking to have your cake and eat it, too. A few lines in */etc/network/interfaces* and removal of Network Manager will do what you want to accomplish quickly and easily.

---

### Post by wonk-o-matic on 2009-12-05
I can set up wireless manually, easily enough, as I am a UNIX geek by day, but "[a] few lines in /etc/network/interfaces..." is exactly why I caution Windows users to tread carefully when tempted by Linux.  

Controlling access to functions is pretty straightforward stuff, in a *nix environment - even just with group rights and sudo, not to mention even more security functionality added through pam modules.  What I want is relatively easy to do, perhaps as simple as file permissions.  

The majority of parents don't allow unbridled computer access to their children.  Why does Canonical think that it can someday own the desktop if they continue to ignore the fact that the majority of computers are used by families, not college students?

---

### Post by chili555 on 2009-12-05
That's a complicated issue you are raising. For instance:> Why does Canonical think that it can someday own the desktopI am not aware that they *do* want to 'own the desktop.' Do you have a citation?> the majority of computers are used by families, not college students? I am also not aware of any demographics which support or refute that claim. By families, do you mean families with children that need guidance and limits? If so, then I doubt that the assertion is true. My spuse and I are in neither category. We both use and love Ubuntu.

My biggest issue, however, is that you seem to want to bend Ubuntu to be more like Windows at a fundamental level. There is absolutely nothing wrong with that; I will defend to the death your right to do so. It may take years and may never happen at all. Meanwhile, the kids are going places and doing things on the neighbor's wireless access point that we don't want.

In the meantime:> A few lines in /etc/network/interfaces and removal of Network Manager will do what you want to accomplish quickly and easily.

DISCLAIMER: I do not represent Canonical or this forum. My opinions are mine and mine alone.

End rant.

---

### Post by wonk-o-matic on 2009-12-05
"Owning the desktop" doesn't seem to big a leap from : > Ubuntu 9.10 brings changes small and large that all have a common purpose - to make Ubuntu the most user-friendly operating system available.- [http://www.ubuntu.com/news]("http://www.ubuntu.com/news")

and:

> "We definitely shouldn't give up the desktop," Shuttleworth said. "This is one of the most exciting years for the desktop in living memory." - [http://itmanagement.earthweb.com/osrc/article.php/3840941/Shuttleworth-Linux-Desktop-in-Most-Exciting-Year.htm]("http://itmanagement.earthweb.com/osrc/article.php/3840941/Shuttleworth-Linux-Desktop-in-Most-Exciting-Year.htm")

but admittedly my expression (and a typical expression from the Linux community, at large.)

Also note from Network Manager's own site:
> You should never need to use the command line or configuration files to manage your network (unless you want to!);  - [http://projects.gnome.org/NetworkManager/]("http://projects.gnome.org/NetworkManager/")

And, in fact, that makes it "more like Windows", which is why I hated Network Manager in the beginning, because I don't know anything about its configuration files: can I tweak them by hand, how do I do the things I've always done?  

As for who is using computers, it may be true that business users are the most common, or some other group.  Not everyone has as many computers sitting around the house as I do.  Going after school students was a strategy that seemed successful for Apple, anyways.  

Whatever the case, more-Windows-like (in terms of GUI configuration) is the Ubuntu direction, from everything we see, such as Network Manager.  Being able to connect wirelessly on boot isn't an unreasonable request, nor is locking down the access point, whether for home or business.

I think Network Manager developers are more the people to answer this concern, and there's a Fedora post that at least sounds like it might get this thing started at boot.

---

### Post by chili555 on 2009-12-05
> might get this thing started at boot.It's fairly easy, depending on how you define 'on boot.' If you want it to connect, albeit a bit slowly, without user intervention, right-click the Network Manager icon and select 'Edit Connections.' Select 'Wireless' and select your network. Click 'Edit' and check 'Connect Automatically.' Since this is not a privileged operation, anything I can do, my grand-daughter can undo.

Locking down the specific network is not a default action in NM, as far as I can see.

---

### Post by wonk-o-matic on 2009-12-05
Thanks.  

I have been testing that out.  I checked that box, and then rebooted.  There's a wlan0 in ifconfig, but without an IP4 address.  

Still, that checkbox looks like the sort of thing I need to do.  If that doesn't do what I need, I'll try it in gksudo.  Maybe then, when the box comes up, some daemon will say, "gotta connect."  

I'm actually thinking about downloading the source and looking around for ideas.  I'm still hoping that a slightly different configuration of the package would allow exactly what I want, or at least I might learn that there's a config file I can peer into.  There's always a way.

---

