---
title: "Sound juicer can't query server?"
date: 2007-12-12
forum: Multimedia &amp; Video
---

### Post by curtw on 2007-12-12
Hi:

I searched for similar problems, but didn't see anything that would directly help me (here or  via a general Google search).

When I insert an audio CD and bring up sound-juicer, it tries to retrieve track information, but this fails.  The message I'm seeing is

         This CD could not be queried: Cannot send/receive to/from server.

But I can successfully navigate to [http://musicbrainz.org/](http://musicbrainz.org/) in Firefox.  In fact, if I click on

    Disc->Submit Track Names

in sound-juicer, I'm sent to a musicbrainz page in Firefox that correctly identifies my CD.

So...  Why can't sound-juicer itself retrieve track info??  Am I missing something in the configuration?  I've set the same proxy setting in the Gnome desktop ("System->Network->Network Proxy") as I have in Firefox.

Ideas?

Thanks,
Curt

---

### Post by rrm3 on 2007-12-22
Same thing is happening to me.  :-(

---

### Post by rrm3 on 2007-12-27
Are you by any chance running firestarter?  I'm not very technically oriented, so I don't know why this is happening, but when I stop firestarter, sound-juicer can query the cd track names, but it can't when firestarter is running.  I hope that helps.

---

### Post by Douglas Royds on 2008-01-14
Are you on a corporate network, behind a firewall? Are you behind a firewall on your own private network? Very likely, your problem is to do with your HTTP proxy settings.

In Firefox, go to Edit, Preferences, Advanced, Network, Connection, Settings. If there is a Manual Proxy Configuration HTTP Proxy, or an Automatic proxy configuration URL configured, then copy the HTTP proxy setting or URL.

Open Alt-F1, System, Preferences, Network Proxy, Proxy Configuration. Select either Manual or Automatic proxy configuration (the same as in Firefox), and paste in the Proxy IP address and port number, or the URL as appropriate.

This should allow both Sound Juicer and Rhythmbox to access remote hosts as appropriate.

---

