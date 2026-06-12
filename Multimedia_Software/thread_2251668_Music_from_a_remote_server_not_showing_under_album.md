---
title: "Music from a remote server not showing under album, artist"
date: 2014-11-05
forum: Multimedia Software
---

### Post by goodstuff9 on 2014-11-05
Ubuntu 14.04, Rhythmbox 3.0.1

On another PC (running Lubuntu 14.04), I am running MediaTomb.  

On the Ubunut 14.04 machine, when I start up Rhythmbox 3.0.1, in the "Shared" category, Rhythmbox recognizes the signal from the MediaTomb server on the Lubuntu machine.  If I try to list all songs, it does that just fine.  But, if I click on the category for "Album", or "Artist", it will list the album or artist just fine, but in the far right pane where it should show the songs, it doesn't show anything.  

I don't know how to fix this problem.

---

### Post by tgalati4 on 2014-11-06
Use *easytag* to check the ID3 tags.  If they are blank, then they don't get indexed properly in *mediatomb*.

---

### Post by goodstuff9 on 2014-11-06
Thanks, but I don't think that is the issue.  The songs appear to be properly tagged.  Also, using apps on my smartphone, I *CAN* see the songs from that same MediaTomb server categorized by album, artist, etc., perfectly.  So, I think that tells me that things are tagged properly for MediaTomb, and that the problem has something to do with Rhythmbox and/or Grilo and/or ????????

---

### Post by tgalati4 on 2014-11-06
What version of mediatomb?  It could be a bug that needs to be filed if you can demonstrate the problem repeatedly and if others are having the same problem.  I am running an older version of mediatomb on a freenas server and it seems to work fine using 14.04, but I will test it again to see if my collection has a similar problem.

It's possible that your mediatomb index is corrupted.  You might consider deleting it and recreating it.

---

### Post by goodstuff9 on 2014-11-06
Hi, thanks again.  

I'm running version 0.1.12 of MediaTomb.  

I did start with a fresh creation of the database as you suggested, still the same problem.  

However, on my mobile devices, they do not have this problem.

---

### Post by tgalati4 on 2014-11-07
Open a terminal:

```
rhythmbox --debug
```

Pull the terminal to the top (keep on top) and look for error messages related to DAAP when you are selecting a track from a music share.  It works fine in my setup, but I only have 13k tracks.  How many tracks in your mediatomb?  Perhaps you hit a limit in rhythmbox?  Understand, that it takes quite a while to load the entire index into rhythmbox.  The song list gets dumped right away.  So perhaps wait longer?

---

### Post by goodstuff9 on 2014-11-07
I have only 8500 tracks.  

I have waited up to 15 minutes.  

In the terminal are TONS of messages.  When I try to expand by album, I see this message:  

(15:37:41) [0x1b414c0] [rb_audioscrobbler_should_handshake] rb-audioscrobbler.c:840: No username set



But, I see that message popping up all the time.  I didn't see any DAAP related messages.....  But they flew by in the terminal very fast.

---

### Post by tgalati4 on 2014-11-07
audioscrobbling is for use with the last.fm plug-in.  It keeps track of what tracks you have played and sends them to last.fm.  If you haven't set up an account in the plug-in settings, then don't worry about it.  You can try running without the --debug switch and see if any major errors come up first.  It should only take 1 or 2 minutes to load 8500 tracks, so something else is going on.

These are the errors that I get when bringing in my mediatomb library with 931 artists and 13k tracks:

> tgalati4@Mint14-Extensa ~/Desktop $ rhythmbox

(rhythmbox:27103): Rhythmbox-WARNING **: Unable to grab media player keys: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SettingsDaemon was not provided by any .service files

(rhythmbox:27103): libsoup-WARNING **: (soup-uri.c:168):soup_uri_new_with_base: runtime check failed: (SOUP_URI_IS_VALID (base))

(rhythmbox:27103): libsoup-WARNING **: (soup-uri.c:168):soup_uri_new_with_base: runtime check failed: (SOUP_URI_IS_VALID (base))

(rhythmbox:27103): libsoup-WARNING **: (soup-uri.c:168):soup_uri_new_with_base: runtime check failed: (SOUP_URI_IS_VALID (base))

(rhythmbox:27103): libsoup-WARNING **: (soup-uri.c:168):soup_uri_new_with_base: runtime check failed: (SOUP_URI_IS_VALID (base))

(rhythmbox:27103): libsoup-WARNING **: (soup-uri.c:168):soup_uri_new_with_base: runtime check failed: (SOUP_URI_IS_VALID (base))

(rhythmbox:27103): libsoup-WARNING **: (soup-uri.c:168):soup_uri_new_with_base: runtime check failed: (SOUP_URI_IS_VALID (base))


I don't know what the errors mean, but the indexing seems to work fine.  Of course with the --debug switch there is A LOT more output. 

You can use a filter:

```
rhythmbox --debug --debug-match=DAAP
```

It slows down the debugging output as well so you can see individual music tracks getting loaded into the rhythmbox database.

---

### Post by goodstuff9 on 2014-11-08
Are you sure you provided the correct terminal command?  I copy and pasted it, so I know I entered the command exactly as you typed it.....  It looks like thousands of messages flew by in the terminal at a VERY fast speed.  

Anyway, it did not show only DAAP related messages.  I didn't see anything related to DAAP in the message I could figure out.

---

### Post by tgalati4 on 2014-11-09
You are correct.  That switch is either not working or not working as the documentation suggests:

```
man rhythmbox
```

I tried DAAP and "DAAP", neither seemed to filter the output correctly.  I also tried piping with grep but that did not work either.  So I would set your terminal line buffer to 2000 lines and let it run and then scroll back through to see if there are indexing errors.

Check the index using a webpage then check for error messages on the computer hosting mediatomb in /var/log.  [https://help.ubuntu.com/community/MediaTomb](https://help.ubuntu.com/community/MediaTomb)

---

### Post by goodstuff9 on 2014-11-09
Thank you again for helping me out.  

The /var/log file on the hosting computer showed no error or problem messages.  

In a terminal I again ran rhythmbox --debug, but this time I captured ALL the messages from the terminal and put them into a text file that I saved.  Then, I did searches.  

When I searched for "error", nothing interesting came up.  

When I searched for DAAP, these messages appeared:  


(12:48:06) [0x17f80c0] [rb_daap_plugin_init] rb-daap-plugin.c:151: RBDaapPlugin initialising
(12:48:06) [0x17f80c0] [extension_added_cb] rb-shell.c:786: activating extension DAAP Music Sharing
(12:48:06) [0x17f80c0] [create_share] rb-daap-sharing.c:90: initialize daap sharing

(rhythmbox:10253): GLib-GObject-CRITICAL **: object SoupServer 0x224a500 finalized while still in-construction

(rhythmbox:10253): GLib-GObject-CRITICAL **: Custom constructor for class SoupServer returned NULL (which is invalid). Please use GInitable instead.
(12:48:06) [0x17f80c0] [libdmapsharing_debug] rb-daap-plugin.c:472: Unable to start music sharing server (IPv4)
(12:48:06) [0x17f80c0] [libdmapsharing_debug] rb-daap-plugin.c:472: Started DMAP server on port 3689 (IPv6: yes, explicit IPv4: no)
(12:48:06) [0x17f80c0] [libdmapsharing_debug] rb-daap-plugin.c:472: Published DMAP server information to mdns
(12:48:06) [0x17f80c0] [libdmapsharing_debug] rb-daap-plugin.c:472: Starting DACP server

(rhythmbox:10253): GLib-GObject-CRITICAL **: object SoupServer 0x224a5a0 finalized while still in-construction

(rhythmbox:10253): GLib-GObject-CRITICAL **: Custom constructor for class SoupServer returned NULL (which is invalid). Please use GInitable instead.
(12:48:06) [0x17f80c0] [libdmapsharing_debug] rb-daap-plugin.c:472: Unable to start music sharing server on port 3689, trying any open port

(rhythmbox:10253): GLib-GObject-CRITICAL **: object SoupServer 0x224a6e0 finalized while still in-construction

(rhythmbox:10253): GLib-GObject-CRITICAL **: Custom constructor for class SoupServer returned NULL (which is invalid). Please use GInitable instead.
(12:48:06) [0x17f80c0] [libdmapsharing_debug] rb-daap-plugin.c:472: Unable to start music sharing server (IPv4)
(12:48:06) [0x17f80c0] [libdmapsharing_debug] rb-daap-plugin.c:472: Started DMAP server on port 43664 (IPv6: yes, explicit IPv4: no)
(12:48:06) [0x17f80c0] [libdmapsharing_debug] rb-daap-plugin.c:472: Published DMAP server information to mdns

...........

(12:48:08) [0x17f80c0] [libdmapsharing_debug] rb-daap-plugin.c:472: Ignoring local service main1's Music
(12:48:08) [0x17f80c0] [libdmapsharing_debug] rb-daap-plugin.c:472: Ignoring local service main1's Music
(12:48:08) [0x17f80c0] [libdmapsharing_debug] rb-daap-plugin.c:472: Ignoring local service main1's Music
(12:48:08) [0x17f80c0] [libdmapsharing_debug] rb-daap-plugin.c:472: Ignoring local service main1's Music




But, when in Rhythmbox I tried to browse by artist within the MediaTomb songs, these strange messages appeared: 


(12:53:51) [0x17f80c0] [media_browse_next] rb-grilo-source.c:883: next media_browse op for MediaTomb (50)
(12:53:52) [0x17f80c0] [grilo_media_browse_cb] rb-grilo-source.c:848: didn't find any media in Artists, giving up

---

### Post by tgalati4 on 2014-11-09
It's not clear to me if rhythmbox sends a query to mediatomb to search by artist and mediatomb is not correctly interpreting that message?  Or, if the entire music index is being sent from mediabox to rhythmbox and rhythmbox is having trouble creating the songs-by-artist query within rhythmbox.

I don't know enough about DAAP, DMAP, DACP to comment on the error messages.  It appears that the DAAP server did not get started (for what ever reason) and that a backup share called DMAP was used instead.  Perhaps DMAP can't handle songs-by-artist query.  I just don't know.

There are several other music players.  Try a few others to see if they behave the same.  On some players you need to turn on DAAP plug-ins to be able to see network music shares.

---

