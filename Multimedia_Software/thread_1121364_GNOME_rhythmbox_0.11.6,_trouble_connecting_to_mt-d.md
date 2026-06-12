---
title: "GNOME rhythmbox 0.11.6, trouble connecting to mt-daapd"
date: 2009-04-09
forum: Multimedia Software
---

### Post by bartonski on 2009-04-09
I'm running Ubuntu Intrepid Ibex. I'm trying to connect GNOME rhythmbox 0.11.6 to a daap share hosted on a separate debian box, running mt-daapd.

I have consulted Mr. Google:

[Firewall Issues:]("http://ubuntuforums.org/showthread.php?t=187708")
Nope, All ports are open on my firewall.

[URL="http://ubuntuforums.org/archive/index.php/t-350032.html"]
Trouble finding Daap Share run by same user:[/URL]
Nope, the daap server is running on a separate machine.

[Trouble connecting to itunes 7]("http://https://bugs.launchpad.net/rhythmbox/+bug/62842")
Nope, I'm connecting to mt-daapd.

I can connect to the mt-daapd share from itunes, running from an XP box on my network.

I can't see the mt-daapd share when I start rhythmbox, but I can connect using the menu item Music -> Connect to DAAP Share.

When I connect, I cannot see any music.

avahi-daemon is running.


Here are what seem to be the relevant lines from rhythmbox -d daap:
(23:20:23) [0x928f408] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin DAAP Music Sharing loaded
(23:20:23) [0x928f408] [rb_module_init] rb-module.c:140: RBModule 0x98f3d20 initialising
(23:20:23) [0x928f408] [rb_module_load] rb-module.c:72: Loading /usr/lib/rhythmbox/plugins/daap/libdaap.so
(23:20:23) [0x928f408] [register_rb_plugin] rb-daap-plugin.c:112: Registering plugin RBDaapPlugin
(23:20:23) [0x928f408] [rb_module_new_object] rb-module.c:125: Creating object of type RBDaapPlugin
(23:20:23) [0x928f408] [rb_daap_plugin_init] rb-daap-plugin.c:151: RBDaapPlugin initialising
(23:20:23) [0x928f408] [rb_plugin_find_file] rb-plugin.c:263: found '/usr/lib/rhythmbox/plugins/daap/daap-ui.xml' when searching for file 'daap-ui.xml' for plugin 'daap'

...
(23:20:40) [0x928f408] [new_daap_share_resolve_cb] rb-daap-plugin.c:607: adding manually specified DAAP share at debian.localhost
(23:20:40) [0x928f408] [mdns_service_added] rb-daap-plugin.c:433: New service: debian.localhost name=debian.localhost host=192.168.1.97 port=3689 password=0
(23:20:40) [0x928f408] [rhythmdb_tree_entry_type_registered] rhythmdb-tree.c:2676: no entries of newly registered type daap:debian.localhost:debian.localhost:192.168.1.97 loaded from db

Any insights welcome.

---

### Post by bartonski on 2009-04-11
I double checked my firewall settings, and specifically opened ports 3689 (DAAP) and 5353 (mDNS), just as a belt and suspenders move.

I ran 'avahi-browse -a' from the laptop:

tiger@debra-laptop:~$ avahi-browse -a
+ wlan0 IPv4 debian                                        iTunes Audio Access local
+ wlan0 IPv4 debian                                        Web Site local
+ wlan0 IPv4 debian                                        _rsp._tcp local
+ wlan0 IPv4 debian [00:c0:f0:35:88:27]                    Workstation local

So I know that I'm seeing the Daap share on the laptop.

I ran rhythmbox again, hoping that perhaps I had been mistaken about the firewall, and that opening those two ports would make life happy, but I'm still seeing the same results: I can open the share when I explicitly specify which host has the DAAP share, but I still don't see any music.

---

### Post by bartonski on 2009-04-13
**sigh**. It helps when mt-daapd is configured correctly...

I had the mp3dir set to a directory where I didn't have correct permissions; I made that change just before I started working with rhythmbox, and never booted back into XP to test. I happened to boot the machine into XP this morning, found that iTunes wasn't loading music correctly either, and then worked backwards from there.

Note to self: test assumptions before posting on the innwerwebs...

---

