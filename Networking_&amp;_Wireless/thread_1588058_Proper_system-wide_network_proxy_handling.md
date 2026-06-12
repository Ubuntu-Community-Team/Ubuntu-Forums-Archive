---
title: "Proper system-wide network proxy handling"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by bidd on 2010-10-04
I frequently change location between work and home. Work has a non-transparent proxy so I have to manually set http_proxy etc when I'm connected to that domain. At home my connection is direct. When I leave work I shut the lid of my laptop and suspend it. When I'm at home I just open the lid and carry on. Well I'd like to 'just carry on' but I have to manually go through and change:

    gnome proxy settings
    kde proxy settings
    /etc/subversion/servers
    /etc/clamav/freshclam.conf
    /etc/chef/client.rb
    Maven settings
    skype

and so on. It's painful. 

In an ideal world, network manager would store your proxy settings per domain (I think OS X does it this way) and just deal with it system-wide, apps don't need to be aware.

So I've ended up writing my own little network manager script that reconfigures privoxy when a network connection is started (and it switches between direct and the work domain's proxy). With this solution I have manually set all of the proxy settings to 127.0.0.1:8118 in the places listed above, which admittedly I have to do only once.

But unfortunately that's not the full story. 

When daemons are started via init, they don't inherit the environment settings from /etc/environment (the ubuntu wiki says /etc/environment is the place for system wide but I don't think it is). Consequently, services can't read the http_proxy env var. For each of those you have to manually set the proxy. 

In addition, when I do a sudo service restart, the http_proxy env var isn't set, yet again the services can't read http_proxy (unless I change /etc/sudoers to preserve http_proxy).

I accept it's probably a security risk but why can't all shells read http_proxy? A lot of the daemons we're using here need to connect to the internet and it just seems there must be a better way. Do I have to weed out every config file and set up the proxy?

Am I missing something? 

This just feels so clunky in this day and age. Can we do something at the network stack layer via network manager so it's properly system-wide and transparent? I realise daemons with persistent connections might still be a problem when switching location but they should recover.

Last time I checked there was a whole bunch of software in Ubuntu by default which doesn't support a proxy. Empathy springs to mind. If Canonical/Ubuntu are serious about the enterprise, this whole area needs streamlining.

I've searched the forums for http_proxy and it seems to be a particular pain point for a lot of people and deserving of considerable attention.

---

### Post by xv1700 on 2010-10-04
+1 I have been trying to push Ubuntu in the enterprise for years and this really sours the message.

---

