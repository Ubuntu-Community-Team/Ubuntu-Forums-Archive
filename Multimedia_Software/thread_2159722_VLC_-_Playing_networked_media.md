---
title: "VLC - Playing networked media"
date: 2013-07-04
forum: Multimedia Software
---

### Post by Geffers on 2013-07-04
All my searches seem to explain how to use VLC to stream media but now how to play networked media files.

I have minidlna running on a small stand alone Raspberry Pi, all my media clients see and play fine but I'd like to be able to play files on my Ubuntu laptop, ideally using VLC

Now my media clients find it easily but the minidlna config file shows it servers on port 8200.

I have tried entering network addresses of every variation including/ommiting port number, full filepath or device filepath, all to no avail.

Where am I going wrong :(

Geffers

---

### Post by dannyboy79 on 2013-07-05
which version of VLC are you trying to use? Have you tried going in the menu bar select "View" and then "Playlist". In the new window click on the "triangle" before the text "Local Network" on the left. The menu is expanded and there you should see the entry "Universal Plug'n'Play". Now select "Universal Plug'n'Play" and wait...it takes at least 20 seconds (but may also take some minutes until the server shows up).

---

### Post by Geffers on 2013-07-06
> **dannyboy79 said:**
> which version of VLC are you trying to use? Have you tried going in the menu bar select "View" and then "Playlist". In the new window click on the "triangle" before the text "Local Network" on the left. The menu is expanded and there you should see the entry "Universal Plug'n'Play". Now select "Universal Plug'n'Play" and wait...it takes at least 20 seconds (but may also take some minutes until the server shows up).

Thanks DannyBoy, that seems to have sorted it.

It seems I have VLC media player 2.0.5 Twoflower, strangely the 'view' option just seems to show or hide the window without a tick on the menu options.

I think that has sorted it, thanks.

Geoff

---

### Post by Geffers on 2013-07-07
> **Geffers said:**
> Thanks DannyBoy, that seems to have sorted it.

It seems I have VLC media player 2.0.5 Twoflower, strangely the 'view' option just seems to show or hide the window without a tick on the menu options.

I think that has sorted it, thanks.

Geoff

DannyBoy, you might have an opinion on this; your reply has been most useful but what I was actually aiming for was to allow a friend to VPN to my computer then share my playlists.

Now she connects OK, gets an IP address within my network but the upnp option did not show up my media server on her VLC.

Should work but I suppose effectively she is on two networks, her own and my VPN.

If you have any ideas I'd appreciate it, I am running minidlna on my home network.

I am going to post another post with a different Title as this one was VLC specific.

Geffers

---

