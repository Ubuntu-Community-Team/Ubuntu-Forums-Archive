---
title: "sharing SANE with Windows"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by khyd on 2010-04-14
Hello,

I have manage to setup sane and xsane and I can scan from the linux box where the scanner is plugged in. 

Though, on my windows terminal server, I do launch Twain Sane which seems to connect but report NO DEVICES FOUND ON BACKEND.

From that server I can telnet my linux box with the port 6566.

On that Linux box, I have xinet installed and configure according to some HOWTO I found:
[http://hardc0l2e.wordpress.com/2009/07/10/sane-sharing-in-ubuntu/](http://hardc0l2e.wordpress.com/2009/07/10/sane-sharing-in-ubuntu/)
[http://penguin-breeder.org/sane/saned/](http://penguin-breeder.org/sane/saned/)
but nothing works, always the same problem.

FYI: I have installed Ubuntu Minimal with no server option on it and then entered the following command line to install what was necessary (what I think is):
sudo apt-get install xorg xterm gdm menu gksu synaptic rdesktop sane xsane network-manager-gnome cups system-config-printer-gnome xinetd xfce4 update-manager samba dillo

Thank you for your help, I really would like to make this SANE work with my Windows Terminal Server.

Regards,
Yael

---

