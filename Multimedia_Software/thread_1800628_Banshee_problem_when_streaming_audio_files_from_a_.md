---
title: "Banshee problem when streaming audio files from a DAAP share..."
date: 2011-07-09
forum: Multimedia Software
---

### Post by Midnight Star on 2011-07-09
I've got a small problem with Banshee that I need some help with, if possible. I'm currently using the latest version of Ubuntu 11.04 and it's up to date. The problem i'm having is with Banshee playing music files over my DAAP share. My DAAP server is running Firefly (mt-daapd), and Banshee can see the server and shares just fine. It loads the song list from the server, but when I select a song to play it just sits there. Rhythmbox works just fine, sees the share and plays the songs ok (which is what i've fallen back to for the moment), so I know it's not a hardware or software problem from the sound "system".

Other features of Banshee play just fine, including internet radio stations, internet archives, and importing songs from the server (which makes the song local instead of networked from a single source). Ok, so streaming from the DAAP share isn't working; here's the output from the terninal I started Banshee from:

[-----START-----]
[Info  07:13:23.440] Running Banshee 2.0.0: [Ubuntu 11.04 (linux-gnu, i686) @ 2011-06-28 05:46:57 UTC]
[Info  07:13:28.765] Updating web proxy from GConf
[Info  07:13:28.998] All services are started 4.668005
** (Banshee:2341): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:2341): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'

** (Banshee:2341): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 992, in get_info
    return self.syncdaemon_folders.get_info(path)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 634, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 773, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/michael/.ubuntuone/Purchased from Ubuntu One'


** (Banshee:2341): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

** (Banshee:2341): WARNING **: Error rescanning Purchased Music: No such file or directory
** (Banshee:2341): DEBUG: Loading the real store page

** (Banshee:2341): WARNING **: Got less number of items in credentials hash table than expected!
[Info  07:13:32.802] nereid Client Started
[Info  07:13:33.176] GStreamer version 0.10.32.0, gapless: True, replaygain: False
[Info  07:13:33.389] AppleDeviceSource is ignoring unmounted volume 77 GB Filesystem
[-----END-----]

The log above includes attempting to stream at least 2 songs from the DAAP server (i've tried more with the same results). There's no other "text" message after "AppleDeviceSource" (which is the last message before I attempted to stream the music files), that indicates a problem.

One extra note, if I look at the properties of a song from my DAAP share in Banshee, it shows the song title, artist, album and file size, but the URI doesn't show the IP Address of the server, it shows:

[http://127.0.0.1:8089/2037343232/6188](http://127.0.0.1:8089/2037343232/6188)

It's like the path to the song is defaulting to a "local" proxy, but I don't have the Banshee software configured that way: I'm using the default installation configuration. All the songs from the DAAP share show the "proxy" ip and port with different identifiers after that. 

Perhaps that's why Banshee was loading multiple copies of the same DAAP library - it sees the URI from the media server, then stores it in an incorrect "proxy" address. If thats the case, it would load the library again, doubling the number of songs since it wouldn't be able to match the songs URI (they'd be two different addresses).

---

### Post by Midnight Star on 2011-07-09
Still working to debug this one, this is what i've discovered so far...

In the mt-daapd log (firefly's log file) it's reporting when songs are selected from Banshee:

Thread 0: Bad arg:
Thread 0: Bad arg:
Thread 0: Bad arg:
Thread 0: Bad arg:

I'll see if I can get a "verbose" option for firefly, since the argument being reported in the log file now is blank.

---

### Post by Midnight Star on 2011-07-09
Ok, running firefly (mt-daapd) at debugging level 9 doesn't show anything useful, especially the actual parameters being passed to mt-daapd from Banshee: just shows "Bad Arg:" along with: 

Could not read: Unknown Internal Error
Could not read: Unknown Error

I'd really be interested in seeing the arguments being parsed to mt-daapd. Is there a way to do this using startup parameters?

---

### Post by matthewboh on 2011-07-09
I'm having the exact same problem!

---

### Post by Midnight Star on 2011-07-09
It's strange. It's happening on two different motherboard/cpu combos, and even on a third computer with just the base ubuntu 11.04 release on it (no extras like jack or audio control extras). Hopefully someone can get back with us on how to debug this, or at least get some debug information to those maintaining it.

---

### Post by Midnight Star on 2011-07-09
Ok, I think i've solved this one for me and possibly others. I'll keep tabs on it over time and see if its a solution or a fluke of sorts. On all my computers I use custom set of iptables rules. I added the following:

sudo iptables -I INPUT 1 -s 127.0.0.1 -j ACCEPT

Now, streaming is working. :-) Silly I know, but I didn't include the loopback device as a firewall rule. Of course the above is only temporary, and all iptables changes will be lost on reboot, so be sure to make the change permanent (survives reboot).

I hope this helps others having a similar problem.

---

