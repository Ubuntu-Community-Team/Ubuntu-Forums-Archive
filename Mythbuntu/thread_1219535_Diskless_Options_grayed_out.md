---
title: "Diskless Options grayed out"
date: 2009-07-21
forum: Mythbuntu
---

### Post by mitchell2345 on 2009-07-21
Hi,

I am running testing + trunk and when i go to system roles in MCC the dhcp server and diskless server are greyed out.  can anyone tell me why?

here is cmd line output:
mitchell@mythtv:~$ mythbuntu-control-centre --debug
/usr/bin/mythbuntu-control-centre:52: GtkWarning: Ignoring the separator setting
  self.glade = gtk.glade.XML(GLADEDIR + '/' + 'mythbuntu_control_centre.glade')

(mythbuntu-control-centre:7902): libglade-WARNING **: could not find a parent that handles internal children for `vbox'
2009-07-21 20:39:21,248 DEBUG: Using plugin root path of : /usr/share/mythbuntu/plugins
2009-07-21 20:39:21,261 DEBUG: Importing plugin:        graphics_drivers
2009-07-21 20:39:21,263 DEBUG: Importing plugin:        plugins
2009-07-21 20:39:21,266 DEBUG: Importing plugin:        proprietary_codecs
2009-07-21 20:39:21,268 DEBUG: Importing plugin:        remote
2009-07-21 20:39:21,271 DEBUG: Importing plugin:        system_roles
2009-07-21 20:39:21,272 DEBUG: Importing plugin:        mysql_configuration
/var/lib/python-support/python2.6/MySQLdb/__init__.py:34: DeprecationWarning: the sets module is deprecated
  from sets import ImmutableSet
2009-07-21 20:39:21,284 DEBUG: Importing plugin:        services
2009-07-21 20:39:21,294 DEBUG: Importing plugin:        themes
2009-07-21 20:39:21,295 DEBUG: Importing plugin:        system_updates
2009-07-21 20:39:21,301 DEBUG: Importing plugin:        startup_behavior
2009-07-21 20:39:21,303 DEBUG: Found the following plugin classes:
2009-07-21 20:39:21,303 DEBUG: [<class 'graphics_drivers.RestrictedDriversPlugin'>, <class 'plugins.MythPluginsPlugin'>, <class 'proprietary_codecs.ProprietaryCodecsPlugin'>, <class 'remote.RemotePlugin'>, <class 'system_roles.SystemRolesPlugin'>, <class 'mysql_configuration.MySQLConfigurationPlugin'>, <class 'services.MCCServices'>, <class 'themes.ThemesPlugin'>, <class 'system_updates.SystemUpdatesPlugin'>, <class 'startup_behavior.LoginPlugin'>]
2009-07-21 20:39:21,325 DEBUG: Found the following plugin instances:
2009-07-21 20:39:21,325 DEBUG: [<graphics_drivers.RestrictedDriversPlugin object at 0x9b0738c>, <plugins.MythPluginsPlugin object at 0x9c0508c>, <proprietary_codecs.ProprietaryCodecsPlugin object at 0x9c0504c>, <remote.RemotePlugin object at 0x9c050ec>, <system_roles.SystemRolesPlugin object at 0x9c0568c>, <mysql_configuration.MySQLConfigurationPlugin object at 0x9c0576c>, <services.MCCServices object at 0x9c057ac>, <themes.ThemesPlugin object at 0x9c05c6c>, <system_updates.SystemUpdatesPlugin object at 0x9c05bec>, <startup_behavior.LoginPlugin object at 0x9c05bcc>]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
2009-07-21 20:39:22,599 WARNING: Unable to read /etc/mythtv/mythweb-digest

Thanks,
Mitchell

---

### Post by mitchell2345 on 2009-07-31
I have still not found a solution for this.  Kind of disappointed.  I switched to MythBuntu for the "ease of diskless" vs Fedora.  And support with Mythbuntu.

~Mitchell

---

### Post by raptorjr on 2009-08-31
I have the same problem. Anyone found a solution?

---

### Post by mitchell2345 on 2009-08-31
> **raptorjr said:**
> I have the same problem. Anyone found a solution?

yes, the problem is with fixes.  As funny as it sounds.

To correct remove all mythtv related packages.
run dpkg-reconfigure mythbuntu-repos and enable trunk but not fixes.

reinstall packages.

fixed it for me.

Mitchell

---

### Post by raptorjr on 2009-08-31
> **mitchell2345 said:**
> yes, the problem is with fixes.  As funny as it sounds.

To correct remove all mythtv related packages.
run dpkg-reconfigure mythbuntu-repos and enable trunk but not fixes.

reinstall packages.

fixed it for me.

Mitchell

Sounds great. But i'm not that good at Mythbuntu, yet. How do i remove all mythtv packages? Or does "run dpkg-reconfigure mythbuntu-repos" take care of everything?

A little more detailed instructions would be greatly appreciated.

---

### Post by mitchell2345 on 2009-08-31
this should do it:
sudo apt-get remove mythtv*
sudo pkg-reconfigure mythbuntu-repos
sudo apt-get install mythtv*

---

### Post by raptorjr on 2009-09-01
> **mitchell2345 said:**
> this should do it:
sudo apt-get remove mythtv*
sudo pkg-reconfigure mythbuntu-repos
sudo apt-get install mythtv*

Hmm, something is wrong. If i do "sudo apt-get remove mythtv*" all i get is: 

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package mythtv-setup

I thought it was okej and that it was already removed so i continued, but i get the same error when i try to install again.

---

### Post by mitchell2345 on 2009-09-01
ok lets try using the gui.

goto X>System>Synaptic Package manager
do a quick search for Myth

click to uninstall all myth packages that are installed.
now to the dpkg --reconfigure
then from the gui reinstall mythbuntu-common.

---

### Post by raptorjr on 2009-09-01
=( Didnt work for me. Removed everything, did the reconfigure, installed mythbuntu-common and control-center. Diskless Server still grayed out, and no option to configure diskless server.

---

### Post by superm1 on 2009-09-01
Disable the testing repo and remove/reinstall mythbuntu-common and mythbuntu-control-centre.

Diskless isn't fixed yet for the new MCC.

---

### Post by raptorjr on 2009-09-01
> **superm1 said:**
> Disable the testing repo and remove/reinstall mythbuntu-common and mythbuntu-control-centre.

Diskless isn't fixed yet for the new MCC.

Thank you, that worked.

---

