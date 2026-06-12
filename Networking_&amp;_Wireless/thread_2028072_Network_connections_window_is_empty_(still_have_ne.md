---
title: "Network connections window is empty (still have network access)"
date: 2012-07-17
forum: Networking &amp; Wireless
---

### Post by darkcape on 2012-07-17
Running Ubuntu 12.04 

Last week for some reason my network Connections app has stopped working correctly. If looking at it there are no entries in any of the tabs. I still have access to the the network and internet and get a DHCP address and information is populated in ifconfig. 

though the settings and network I see information populated but the options button is greyed out. 

I would however like to get this working together as I cannot create any VPN connections through the Network connections or through the network settings windows always coming up with the error: (connection add failed: Connection not visible or not available) 

I have tried removing packages and bring them back to no avail I've also tried different Desktop managers (Cinnamon, Gnome 2D, and KDE)  and all seem to have the same issue as Unity.

currently working around the VPN connections with using a virtual box and sharing folders inside of it but I'd rather have full control of my network. 

Thanks in advance.

---

### Post by Sergius14 on 2012-07-17
Sometimes I see the similar failure. It is unfrequent but happens once a while.

What I do to solve this is to kill the process and run it again from console.

killall nm-applet

./nm-applet&

(you can close the console and the applet shoud be still running).


It is so unfrequent and after several days suspending the laptop that I just do this to fix it.

---

### Post by darkcape on 2012-07-17
Thanks for the reply. 

not a fix for me though instead I get the following output (try looking for fixes for the beginning errors but most go to bug reports that I have no clue how to work through) :

[FONT=Courier New]Ubuntu 12.04:~$killall nm-applet
Ubuntu 12.04:~$nm-applet&
[1] 3388
Ubuntu 12.04:~$Gtk-Message: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.
** Message: applet now removed from the notification area

(nm-applet:3388): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed[/FONT] [FONT=Courier New]

** (nm-applet:3388): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed[/FONT] [FONT=Courier New]

(nm-applet:3388): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed[/FONT] [FONT=Courier New]

(nm-applet:3388): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed[/FONT] [FONT=Courier New]

** (nm-applet:3388): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed[/FONT] [FONT=Courier New]

(nm-applet:3388): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed[/FONT] [FONT=Courier New]

(nm-applet:3388): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed[/FONT] [FONT=Courier New]

** (nm-applet:3388): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed[/FONT] [FONT=Courier New]

(nm-applet:3388): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed[/FONT] [FONT=Courier New]

(nm-applet:3388): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed[/FONT] [FONT=Courier New]

** (nm-applet:3388): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed[/FONT] [FONT=Courier New]

(nm-applet:3388): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed[/FONT] [FONT=Courier New]

(nm-applet:3388): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed[/FONT] [FONT=Courier New]

** (nm-applet:3388): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed[/FONT] [FONT=Courier New]

(nm-applet:3388): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed[/FONT] [FONT=Courier New]

(nm-applet:3388): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed[/FONT] [FONT=Courier New]

** (nm-applet:3388): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed[/FONT] [FONT=Courier New]

(nm-applet:3388): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed[/FONT] [FONT=Courier New]

(nm-applet:3388): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed[/FONT] [FONT=Courier New]

** (nm-applet:3388): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed[/FONT] [FONT=Courier New]

(nm-applet:3388): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed[/FONT] 

not sure if anyone could find this helpful but since I had the process window still open I get the following when trying to add a new connection.

[FONT=Courier New]Gtk-Message: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.

(nm-connection-editor:5951): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed

** (nm-connection-editor:5951): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed

(nm-connection-editor:5951): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nm-connection-editor:5951): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed

** (nm-connection-editor:5951): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed

(nm-connection-editor:5951): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nm-connection-editor:5951): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed

** (nm-connection-editor:5951): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed

(nm-connection-editor:5951): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nm-connection-editor:5951): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed

** (nm-connection-editor:5951): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed

(nm-connection-editor:5951): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nm-connection-editor:5951): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed

** (nm-connection-editor:5951): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed

(nm-connection-editor:5951): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nm-connection-editor:5951): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed

** (nm-connection-editor:5951): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed

(nm-connection-editor:5951): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nm-connection-editor:5951): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed

** (nm-connection-editor:5951): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed

(nm-connection-editor:5951): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

** (nm-connection-editor:5951): WARNING **: Invalid setting VPN: gateway

** (nm-connection-editor:5951): WARNING **: Invalid setting VPN: gateway

** (nm-connection-editor:5951): WARNING **: Invalid setting VPN: gateway

(nm-applet:3388): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed

** (nm-applet:3388): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed

(nm-applet:3388): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nm-connection-editor:5951): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed

** (nm-connection-editor:5951): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed

(nm-connection-editor:5951): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed[/FONT]

---

### Post by darkcape on 2012-07-17
looking a little closer to some of the errors I went to view what was in /etc/NetworkManager/system-connections/ and found a bunch items in there and I can tell that they were my failed attempts at setting up other network connections. 

if I remove them all. I can see that the main network connection vanishes and goes to off. But is quickly rebuilt after changing it to on again.

---

### Post by Sergius14 on 2012-07-17
it is very strange, seams to have a file or something corrupted.

You can try reinstalling network manager.

try it from console with purge instead of remove (delete configuration files while remove keep it)

sudo apt-get purge network-manager

I sugges a reboot (just in case, to be clean).

and to reinstall it

sudo apt-get install network-manager


And see whats happens,.

---

### Post by darkcape on 2012-07-18
Thanks again, 

un-installed and reinstalled still no love. 

FYI anyone following along make sure you download the network-manager files before removing as this will disable any networking you do have working. 

thinking it might be time to go for a full blown re-installation in the near future.

---

### Post by darkcape on 2012-07-18
fewer errors this time around but still greek to me. 

Ubuntu 12.04:~$ killall nm-applet
Ubuntu 12.04:~$ nm-applet&
[1] 4473
Ubuntu 12.04:~$ Gtk-Message: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.
** Message: applet now removed from the notification area

(nm-applet:4473): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed

** (nm-applet:4473): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed

(nm-applet:4473): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nm-applet:4473): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed

** (nm-applet:4473): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed

(nm-applet:4473): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nm-applet:4473): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed

** (nm-applet:4473): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed

(nm-applet:4473): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nm-applet:4473): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed

** (nm-applet:4473): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed

(nm-applet:4473): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nm-applet:4473): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed

** (nm-applet:4473): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed

(nm-applet:4473): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nm-applet:4473): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed

** (nm-applet:4473): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed

(nm-applet:4473): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area

------ end of start -----
------ error when adding a VPN -----

(nm-applet:4473): GLib-GIO-CRITICAL **: g_async_initable_real_init_finish: assertion `g_simple_async_result_is_valid (res, G_OBJECT (initable), g_async_initable_real_init_async)' failed

** (nm-applet:4473): CRITICAL **: dbus_g_error_has_name: assertion `error != NULL' failed

(nm-applet:4473): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

---

### Post by sid5291 on 2012-07-21
I have been having the same problem for almost a week now. The weird thing is that i can use WICD fine .. and yeah the connections that are dhcp work fine but if i need to edit a connection for static ip its impossible .. 

Like darkcape mentioned a blank edit connections window. With many failed attempts in /etc/NetworkManager/system-connections/

Have you found any solution to this problem ?

Or have you resorted to a full blown reinstall i want to avoid that at all cost if possible ..

Oh yeah and i tried to reinstall nm, set in NetworkManager.conf manage to true .. But nothing is working ..

I am also running ubuntu 12.04

Thanks for any help :)

---

### Post by gestapolur on 2012-07-22
I met same problem too but no solution currently.
some tips may help:

[LIST=1]
[*]I have tried purge & reinstall Network Manager and gnome but no effect.
[*]It's not a privilege problem because I was already in netdev group & root etc.
[*]I met this problem after update or reinstall gnome3.4.2. Before then I upgrade 10.04 LTS to 12.04 LTS
[/LIST]
Any help would be appreciate!

---

### Post by tripialos on 2012-07-26
I also have the same problem.

Anyone found any solution?

12.04 LTS is far the worst release of Ubuntu...actually might be the worst OS at the moment. I used to love Ubuntu but this time they really blow things up.

---

### Post by antono on 2012-07-26
> **tripialos said:**
> I also have the same problem.

Anyone found any solution?

12.04 LTS is far the worst release of Ubuntu...actually might be the worst OS at the moment. I used to love Ubuntu but this time they really blow things up.\


Same problem. Cannot add vpn connection. 12.04LTS

---

### Post by darkcape on 2012-07-27
I've been hoping that recent updates might have a fix but to no avail. 

I plan on a fresh install over the weekend. 

most likely going kubuntu 12.04 this time around (personal preference).  I'll let all know if it works.

---

### Post by murias002 on 2012-07-31
hi. i have exactly the same problem, from 3 weeks ago. same environment, but in 64 bits ubuntu 12.04.

i tried everything possible to fix, some people have a solution ?

---

### Post by printercu on 2012-07-31
Had the same problem & just fixed it.
I've installed gnome3 using ricotz's ppa. Before I had some problems with gnome-shell-extensions so I've downgraded it to gnome3-team ppa packages (maybe it takes a part).
To fix nm problem I've downgraded libglib2.0-0 from ricotz's version to precise-updates.
I've made this by synaptic (package->force version), but I think cli version is ```
sudo apt-get install libglib2.0-0/precise-updates
```

---

### Post by Mitthrawn on 2012-07-31
printercu, how did you downgrade libglib2.0-0 without removing a load of other packages?

I executed the command you posted and apt-get told me that I had to remove a load of packages. Tried Synaptic, aptitude, same thing.

---

### Post by printercu on 2012-07-31
Are they mostly gnome packages? I wrote that i'd downgraded gnome-shell from ricotz's version before, that time it also downgraded 30-40 packages (maybe more).

---

### Post by Mitthrawn on 2012-08-02
Yeah, mostly gnome related packages.
Sorry I don't really get what you mean. You mean you ppa-purge'd ricotz's PPA ?
And what do you mean by "downgraded it to gnome3-team ppa packages" ? There is no "gnome-shell" nor "gnome-shell-extensions" package for Precise in gnome3-team 's PPA.

---

### Post by printercu on 2012-08-02
first I used ricotz repo with ppa:gnome3-team/gnome3 & ppa:noobslab/gnome.
most gnome packages have been installed from ricotz. then i reinstalled gnome without ricotz repo. As I looked now gnome-shell package is from ubuntu's repo & extensions are from noobslab.
Indeed  it does no mater) Ricotz's version of liblglib is the point of nm problem. So if you want get you nm working you should replace it with other one or wait for ricotz to fix it.

---

### Post by Mitthrawn on 2012-08-04
Thanks for your reply.
I think I'll wait for ricotz to fix this problem.

Update: I've just upgraded to the newest version of libglib2.0-0 (released on 8/2) from ricotz's PPA, the problem has been fixed!

---

### Post by darkcape on 2012-08-04
Thanks for the update [Mitthrawn]("http://ubuntuforums.org/member.php?u=852087") the update to libglib2.0-0 worked for me too. Procrastination paid off :-). 

thanks to all and to the ricotz's maintainers if they read this.

---

### Post by lUomino on 2012-11-20
> **Sergius14 said:**
> Sometimes I see the similar failure. It is unfrequent but happens once a while.

What I do to solve this is to kill the process and run it again from console.

killall nm-applet
./nm-applet&

(you can close the console and the applet shoud be still running).

It is so unfrequent and after several days suspending the laptop that I just do this to fix it.

I, too, encounter this problem after my machine (running Ubuntu 12.04, gnome, fully patched) has been running several days, with at least one suspend/resume per day.

It's not troubling enough to me to reconfigure gnome, so I've instead implemented a daily cronjob to reload nm-applet.  However, it would be nice to get this fixed, since it's most probably a buffer overwrite or similar someplace.

One caveat for our less-experienced correspondents: nm-applet is in /usr/bin, so './nm-applet &' above will work only if your working directory is /usr/bin.  A more general solution is 'nm-applet &'.

I'll probably be upgrading to 12.10 this weekend. so I'll report back if this problem is fixed in 12.10.

---

### Post by lUomino on 2012-11-27
> **lUomino said:**
> I, too, encounter this problem after my machine (running Ubuntu 12.04, gnome, fully patched) has been running several days, with at least one suspend/resume per day.

It's not troubling enough to me to reconfigure gnome, so I've instead implemented a daily cronjob to reload nm-applet.  However, it would be nice to get this fixed, since it's most probably a buffer overwrite or similar someplace.

One caveat for our less-experienced correspondents: nm-applet is in /usr/bin, so './nm-applet &' above will work only if your working directory is /usr/bin.  A more general solution is 'nm-applet &'.

I'll probably be upgrading to 12.10 this weekend. so I'll report back if this problem is fixed in 12.10.

I upgraded last Wednesday and stopped the cron job.  Since then, I've put the machine to sleep and woken it up at least daily.  Throughout, nm-applet has continued to work, so I'm calling this fixed, at least for me.

---

### Post by lUomino on 2013-02-01
Alas, it appears that the problem still exists.  So, I've re-enabled the cronjob and await a fix.

---

