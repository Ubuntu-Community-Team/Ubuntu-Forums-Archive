---
title: "Wicd tray icon"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by soropi on 2010-03-11
hallo everyone
I installed "ubuntu minimal" on an old pc and then installed "wicd" , which worked fine at first time. But then after deleting and resetting "gnome" menu bars , trying to settup my system , I suddenly lost "wicd" tray icon , though I can connect to network. I can only load the icon giving ```
wicd-client
``` on terminal.
I tried adding it on "system-preferences-start up programs" but didn't work.
Below I give some error messages I get in terminal :
```
$ wicd-client -n
Importing pynotify failed, notifications disabled.
Has notifications support False
Loading...
Connecting to daemon...
Connected.
/usr/share/wicd/wicd/gui.py:151: GtkWarning: gtk_toolbar_set_icon_size: assertion `icon_size != GTK_ICON_SIZE_INVALID' failed
  self.wTree = gtk.glade.XML(gladefile)
refreshing...

``` That launches "wicd" menu
```
wicd-client -a
Importing pynotify failed, notifications disabled.
Has notifications support False
Loading...
Connecting to daemon...
Connected.
Done loading.

``` That adds an icon in tray. 
I'm a starter in linux so these messages can't help me. 
Thank you in advance

---

### Post by chili555 on 2010-03-11
If you right-click the panel at the top right and add a Notification Area, does it appear?

---

### Post by soropi on 2010-03-11
Thanks for reply.
No , it doesn't add the icon.

---

### Post by soropi on 2010-03-12
> Thanks for reply.
No , it doesn't add the icon.
Any suggestions , on how to load on startup the icon , welcome.

---

### Post by gruvn on 2010-03-14
Just posting to bump this.  I'm having the same problem.  I've got a connection, but nothing in my panel unless I manually add it (wicd-client), but adding this to startup doesn't seem to persist.

Thanks!

---

### Post by gruvn on 2010-03-15
Alrighty then - I lied.

My problem (no status icon in panel) occurred after reinstalling wicd.  I did a bunch of stuff trying to get my network settings to work, and likely lost track of what stuff I had tried, and when.  I just tried adding an entry for wicd-client to the startup, and it worked. And there was much rejoicing.

---

### Post by soropi on 2010-03-16
So, did you get it back on in startup?
If no , my only success is to find a python program (wicd-client.py) which launches the icon, but still cannot make it open in startup, as it asks for root rights. My ubuntu knowledge cannot reach as far.
If you can suggest something or any other friend then perhaps we can manage it.Thanks.

---

### Post by gruvn on 2010-03-18
Hey Soropi - no - I haven't fixed it.  I thought I had, but it's not.  I still have an internet connection, and I'm happy enough with that!

Sorry I can't help.  :(

---

### Post by HobbitTR on 2010-04-10
> **soropi said:**
> So, did you get it back on in startup?
If no , my only success is to find a python program (wicd-client.py) which launches the icon, but still cannot make it open in startup, as it asks for root rights. My ubuntu knowledge cannot reach as far.
If you can suggest something or any other friend then perhaps we can manage it.Thanks.
I had a similar problem, after a restart I got a dbus error message and wicd would not start and my connection did not display of course. I found a solution here:
[http://ubuntuforums.org/showthread.php?t=1243485](http://ubuntuforums.org/showthread.php?t=1243485)

code:
sudo wicd -foe

revealed a parsing error in /etc/wicd/wired-settings.conf -- 
There will probably be a line with an empty "[]" on it, remove that line. 

The daemon started almost immediately, I selected connect (using a wired connection right now). If you create an icon on a panel and put in the Type: pulldown Application and in the Command: slot put wicd-client you can Start the Wicd client with the system tray icon showing.

---

### Post by soropi on 2010-04-10
@ HobbitTR thanks for your help. It has been long ago , so I used to the idea of a problem with no solution. The ```
sudo wicd -foe
``` didn't give me any help:
```
---------------------------
wicd initializing...
---------------------------
wicd is version 1.6.1 426
setting backend to external
trying to load backend external
successfully loaded backend external
trying to load backend external
successfully loaded backend external
Couldn't detect a wireless interface.
setting wireless interface None
automatically detected wired interface eth0
setting wired interface eth1
setting wpa driver wext
setting use global dns to False
setting global dns
global dns servers are None None None
domain is None
search domain is None
setting automatically reconnect when connection drops True
Setting dhcp client to 0
Wireless configuration file found...
Wired configuration file found...
chmoding configuration files 0600...
chowning configuration files root:root...
Using wireless interface...
Using wired interface...eth1

```It stops there.
Your second suggestion , is the one I already use. I 've made an application icon on panel to be loaded on startup , which on clicking left mouse button activates the wicd tray-icon.
I am grateful for your responce  and any further help.

---

### Post by HobbitTR on 2010-04-10
soropi, did you use the terminal to open the conf file?  
code:
sudo gedit /etc/wicd/wired-settings.conf 

See if there is a line with an empty "[]" on it, delete that line, save the file and see if you can click the Connect on wicd. 

I am pretty new to using wicd so if this does not work for you then maybe someone else can help better.

Good luck :)

---

### Post by soropi on 2010-04-10
My fault didn't mention it before. Nothing like that appeared , here's the result if something wrong:
**/etc/wicd/wired-settings.conf**
```
[wired-default]
afterscript = None
use_static_dns = 0
dns3 = None
postdisconnectscript = None
search_domain = None
dns1 = None
dns_domain = None
lastused = False
broadcast = None
default = 0
netmask = None
dns2 = None
beforescript = None
predisconnectscript = None
ip = None
gateway = None
use_global_dns = 0
```I know only few people use wicd , but already had problems with "nm" in my minimal installation
Thanks again!

---

### Post by lisanels47 on 2011-01-17
I fixed it by doing this:

cd /home/myhome/.wicd
touch USE_NOTIFICATIONS

Lisa

---

### Post by rahuman on 2013-01-08
> **lisanels47 said:**
> I fixed it by doing this:

cd /home/myhome/.wicd
touch USE_NOTIFICATIONS

Lisa

Thanks. This solved my problem. Logging off and logging back applied the changes.

---

