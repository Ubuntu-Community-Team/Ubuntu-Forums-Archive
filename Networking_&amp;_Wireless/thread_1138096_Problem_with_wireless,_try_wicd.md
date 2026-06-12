---
title: "Problem with wireless, try wicd"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by Mars73 on 2009-04-26
After installing Jaunty 2 days ago my wireless on both my laptop and desktop I got intermittend problems with the connection.
Besides other things I use my desktop as a samba server, so that my Xbox with XBMC downstairs can play movies wirelessly from my Ubuntu box upstairs.
This worked great with 8.04 and 8.10 but big problems with 9.04.
At first I played with the cache settings in XBMC, which is weird because it was never changed and always worked, no solution there.
After that I played with the smb.conf settings, no solutions there so reverted back to standard smb.conf.
After that I changed settings in my wireless router, changing channels, security etc, same problem.
Then I remembered that in earlier Ubuntu version (been using it since 6.06) I used WICD as my network manager.
So installed that one on both my machines and the world is fine again!
No dropouts, faster reconnects (NM asked for WPA2 when reconnect, WICD does not and just works!), overall fluid movie watching.
So if you're having wireless problems, I can recommend trying WICD first and see if things look brighter again.

sudo apt-get install wicd 
should handle the uninstall of NM and installation of WICD.
Log off and on to get the icon in the taskbar and configure it.

---

