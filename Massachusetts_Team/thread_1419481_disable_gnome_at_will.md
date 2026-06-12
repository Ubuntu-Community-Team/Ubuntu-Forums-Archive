---
title: "disable gnome at will?"
date: 2010-03-01
forum: Massachusetts Team
---

### Post by bhmildy on 2010-03-01
Hi Mass. team!
Cape Cod here!

I'm running 9.10 on a 512 MB RAM PC, and would like to pick up some extra ram every once in a while by shutting down gnome desktop and running apps from command line.

Tried the following w/o success from both terminal inside gnome and [ctrl] +[alt] +[F1]
sudo etc/init.d/gdm stop
[ctrl] + [alt]  [backspace]
sudo pkill Xorg
gdm stop

found that inside [ctrl] + [alt] + [F1] this seems to shut down gnome
sudo service gdm stop
(and this starts)
sudo service gdm start

But I'm not able to run VirtualBox or firefox from command line after I've done that.
I stumbled across something saying that you can't run graphical programs after shutting down gdm.  I don't really know the difference between gdm and gnome and GUIs, and tend to type things into terminals without really knowing what they mean while hoping for the best.

I find it hard to believe that you can't run a nice pretty program like firefox without running an entire humongous graphical desktop program.  Am I barking up the wrong tree here?  Thoughts?

Thanks,
Russ

---

### Post by leftyfb on 2010-03-01
Russ,

In order to run graphical programs (firefox, Virtualbox interface) you need some type of graphics server like the X Windows Service which in ubuntu we use Xorg. These servers allow you to run Graphical programs. 

If you just have a terminal, you can only run terminal or text-only applications. 

Now, there are text only web browsers like lynx or w3m. VirtualBox can also be run in the background from the command line and be connected to over the network from another (graphical) computer using remote desktop or VNC if you have those enabled on the guest machine.

There are lots of other text only or command line applications out there.


If the Gnome window manager which runs on top of Xorg is too bloated for you, there are window managers available you can try. One of the most popular WM's which take less memory is called Xfce. You can install it by typing the following:
sudo apt-get install xubuntu-desktop 

You can then pick the xfce desktop from GDM which is your login manager when your computer first turns on.

You can find out about Gnome, Xfce and other WM's at [http://www.xwinman.org](http://www.xwinman.org)


If you need further explanation, feel free to join us on IRC on irc.freenode in the channel #ubuntu-us-ma. You can use pidgin or xchat to connect to IRC and join our channel.

Welcome to the community :)

leftyfb

---

### Post by bhmildy on 2010-03-02
I had no idea!  Much to read at XWinman.org.   Great tip.  I look forward to joining the IRC.  Much thanks, Russ.

---

