---
title: "KTorrent : seeds 0(0) leechers 0(0)"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by TerenceJ on 2010-09-24
Hi! I'm quite new to Ubuntu. Have been using it only for a few months now. So far KTorrent was working fine.
Since two days back, i lost all the peers for the torrent i was downloading. I don't know what happened. I did install updates for ubuntu that were shown by the update manager, as i always do, but i'm not sure if that is what caused KTorrent to suddenly stop all connections. 
Now all trackers are shown as either connection refused or socket operation timed out.
any help will be appreciated. thanks.
terence.

---

### Post by stoeptegel on 2010-10-15
There can be two reasons for this; either the tracker does not support the torrent anymore(see your torrents tracker tab(red text)), or there are just not peers "logged in" in the torrents swarm.

---

### Post by Kanedagr on 2010-10-18
I have the exact same problem with [TerenceJ]("http://ubuntuforums.org/member.php?u=1154618"). The trackers are fine and there are leechers (cause i saw them from the the webpage). If i try Manual Announce a few leechers appear for 2 or 3 seconds and then disappear from the screen. Before yesterday i was seeding full speed but today all of a sudden everything stopped. I do have an open port and everything is set fine!! Any suggestion because i see my ratio dropping if it keeps that way. And another thing, when i am adding a new torrent to download, it starts fine, full download speed, and when it reaches 100% and starts the seeding, then it doesn't connect to anyone.

---

### Post by stoeptegel on 2010-10-24
> **Kanedagr said:**
> I have the exact same problem with [TerenceJ]("http://ubuntuforums.org/member.php?u=1154618"). The trackers are fine and there are leechers (cause i saw them from the the webpage). If i try Manual Announce a few leechers appear for 2 or 3 seconds and then disappear from the screen. Before yesterday i was seeding full speed but today all of a sudden everything stopped. I do have an open port and everything is set fine!! Any suggestion because i see my ratio dropping if it keeps that way. And another thing, when i am adding a new torrent to download, it starts fine, full download speed, and when it reaches 100% and starts the seeding, then it doesn't connect to anyone.

I do not know really, but it could be that either you or the other side have their bittorrent client set for no encryption or encryption, and then no one can make a connection. Or you have just too many connections setup. (check you configuration of KTorrent)

---

### Post by perspectoff on 2010-10-24
You must also consider your ISP (Comcast, AT&T, etc.).

Many ISPs have taken to throttling torrent traffic over known torrent ports.

The symptom is starting to download, and then freezing (as throttling kicks in). 

Clearly, firewalls can influence access, as well. Torrent chunks come through many different ports. In general you need all your ports open (unblocked, that is) to use KTorrent (or other torrent program) effectively. 

If you only have some ports unblocked and traffic starts through those ports, but then new chunks come through other ports and you don't have those unblocked, then the symptom will also be torrents starting to come, and then freezing.

---

### Post by ubuntu27 on 2010-10-24
Open KTorrent
Go to SETTINGS----->Configure Ktorrent----->Network

[Check] Use µTorrent protocol.  [UNCheck] Only use µTorrent

Bittorrent ------> 
[Check] Use DHT for additional peers. 
[Check] Use Peerexchange.

[Check] Use protocol encryption.
[Check] Allow unencrypted connection

[Check] Recheck chunks during uploading
[Check] Check data when download is finished

---

