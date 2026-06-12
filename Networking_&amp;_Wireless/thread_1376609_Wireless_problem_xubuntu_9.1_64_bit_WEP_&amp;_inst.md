---
title: "Wireless problem xubuntu 9.1 64 bit WEP &amp; install WICD without internet connection"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by forest_dog on 2010-01-09
I've installed xubuntu 9.1 on to an old pc of mine.  Previously I had ubuntu 9.04 installed without a hitch, worked out of the box, however I thought it was running a bit slow and opted to uninstall and go for the more lightweight xubuntu.

My problem is that xubuntu is not connecting to my wireless network.  It can see my wireless network but when I put in the correct key it does not connect to the internet.  I have done some research and found a possible solution.

It seems that xubuntu/ubuntu has a problem with 64 bit WEP's.  And that installing WICD is might be the solution.

[http://ubuntuforums.org/showthread.php?t=974272](http://ubuntuforums.org/showthread.php?t=974272)

[http://ubuntuforums.org/showthread.php?t=582445](http://ubuntuforums.org/showthread.php?t=582445)

The machine I'm using does not have a network card, so I can't have a wired connection to install WICD.  I have however downloaded a tar.bz2 file from [http://sourceforge.net/projects/wicd/files/](http://sourceforge.net/projects/wicd/files/)  and unzipped it to a directory on the desktop.

I'm a bit of a newbie and i'm not great running commands from terminal.  I've done a few installs of ubuntu, but suck on terminal.  Just need a little bit of help to get over the final hurdles.  I've enclosed the install file that came along with WICD.  I don't seem to have the skills to get WICD to install without an internet connection.  If anybody could help explain what I need to do I would appreciate it.  I've been trying for hours with no luck!

Regards




Installation of Wicd should be done using your distribution package if one
exists.  If not, the installation is relatively straightforward, but there
are a few dependencies:
  1. python (>=2.4, <3.0)
  2. pygtk (>=2.10)
  2. dbus and its glib and python bindings
  3. a dhcp client (dhclient, dhcpcd, and pump are supported)
  4. wireless-tools (iwlist, iwconfig, etcetera)
  5. net-tools (ip, route, etcetera)
  6. a graphical sudo application (gksu, kdesu, and ktsuss are supported),
     while optional, is strongly recommended
  7. urwid (if you want to use the curses client - needs version >=0.9.8.3)
  8. pm-utils (optional for suspend/resume integration)
     Wicd supports using versions >=1.2.4 -- earlier versions may work just
     fine, but they are completely unsupported here.

If you are installing from a bzr pull and you want 
the native language translations, first run this:
  python setup.py update_translations_py
  python setup.py get_translations
You will not need to do this if you're installing from a release tarball.

Next, configure Wicd for installation.  Wicd will, by default, follow the 
FHS guidelines <http://www.pathname.com/fhs/> (or distribution standards 
where applicable if we know about them and it's feasible to implement them).
You can specify exactly where every non-Python file (and some Python files) 
in Wicd will be placed.  Pass "--help" as an option to the following command
for more information, otherwise run it as is to configure Wicd for installation.
  python setup.py configure

Note that setup.py will try to determine if and where to install the autostart
desktop file for kde (either kde3 or kde4, but not both) and where to install
the sleep hook for pm-utils.  

Finally, do the actual installation.  This step will need to be done as
root or with sudo in most cases:
  python setup.py install
If you are packaging Wicd, you will almost surely want to use the "--root"
option; for example:
  python setup.py install --root=/package-dir

To uninstall, you can use (using root or sudo):
  python setup.py uninstall

You *MUST* run "python setup.py configure" before "python setup.py install" -
the "configure" step generates wpath.py from wpath.py.in using the paths 
specified from the arguments to "python setup.py configure". 
As noted above in the configure step, "python setup.py configure" will use 
acceptable defaults, so it is usually not necessary to specify any arguments 
at all.

After installation, especially if Wicd has not been installed before, you 
will probably need to restart the system message bus (dbus) or reload its 
configuration.  You will also need to make sure the Wicd init script is
started at boot.  How to do those things is distribution-dependent, so if 
you're not sure, ask in your distribution's support area(s).

---

### Post by efflandt on 2010-01-09
I have not had any problems with 64-bit WEP with Ubuntu 9.04 or 9.10, Xubuntu 9.10, or Mint 7 or 8 (with automatically recognized wireless or Broadcom STA driver).  Although, at first I misread Network Connections and thought it only did 128-bit after I misread a digit and my 64-bit key did not work.  But after I tried to configure my DSL wireless/modem/router for a 128-bit key and discovering it does not do that, I reread the wireless security settings and noticed that it said 40/128 and 64-bit hex key worked.  My wireless security is through obscurity (wireless in basement which gets up to 2nd floor, but not out past my front porch, and a less common private LAN IP range).

Note that 64-bit WEP is really 40-bit, and 128-bit is really 104-bit.

You forgot to mention any details about the wireless device or related modules you are using.

I believe you have to remove network-manager to use another program to try to connect wireless.

---

### Post by forest_dog on 2010-01-11
I have a router provider from my isp (o2 in the UK) and an Inventel usb wireless dongle.  This is not the problem, wireless manager sees the network fine, and I had it working fine under ubuntu 9.04 out of the box.  I'm thnking of runing xubuntu 9.04 and hope it works better.

---

