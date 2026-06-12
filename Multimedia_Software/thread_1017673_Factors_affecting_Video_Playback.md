---
title: "Factors affecting Video Playback"
date: 2008-12-21
forum: Multimedia Software
---

### Post by woodwose on 2008-12-21
There are a lot of issue that affect video playback.  What I am trying to do is to set up a centralized media libray with dvd images stored on a hard drive array and be able to play any image on any tv or computer in the house.  Here's what I've done over the past couple of months and the conclusions I've reached if anyone else finds them useful.

I picked up two used HP d530S small form factor boxes cheap, one to use as a server, one to use as a client and installed ubuntu on both.  Both have 3.0 GHz Pentium 4's with 512 MB of RAM.  Both come with onboard graphics, but I installed video cards on both, an Nvidia Ge Force FX 5200 on the server and an Nvidia Quadro NVS 400 on the client.  

I also have a Netgear gigabit router, so I installed gigabit LAN cards in both.  I didn't want to be gated by my network, but that is actually probably the least of my problems.

The hard drives are connected to the server by usb 2.0, so that is actually more of a limiting factor than the gigbit network is.

The server also acts as the client for my main TV in my TV room.  The client is set up in my bedroom, both are connected to widescreen TV's with VGA input.  I have a ubuntu laptop with a wireless N card and S-video output that can work as a client machine for any other TV in the house.  And my Windows XP work laptop, which has a wired gigabit connection to my home network can play dvd images as well since the server runs the external hard drives as samba shares.  The hard drives are Seatgate drives with NTFS filesystems which play well with both Windows and Ubuntu.

The network transfer speed required to support playback of a normal (not HD) DVD image seems to be around 1.0 MB/s.  I can actually copy a DVD over the network from my client machine through the server to the external hard drives at around 8.0 MB/s.

For some reason, Totem seems to work much better for me than VLC.  I get much smoother playback with Totem.  With VLC I get a lot of jerkiness and skipping, not sure if I have it configured optimally though.  There are certainly a lot more options to tune VLC than there is in Totem.

I was copying a DVD through the server to the hard drives this morning from my client and watching an image from a different hard drive on my client at the same time, and here are the performance stats on my client.

Upload speed averaged around 8.0 MB/s
Download speed averaged around .9 MB/s
CPU Utilization was around 75% 
RAM Utilization was around 315 MB, 62.1% utilized
Swap was around 38.9 MB or 8.5% of 454.9 MB utilized

Yeah, it was a CPU load, but it was copying a dvd and playing one at the same time.  Normally, just during playback the CPU load is around 30-35%.

These are the limiting factors that can affect video playback performance over a network:

1.  Network speed/traffic
2.  Server storage read speed
3.  Server CPU
4.  Server RAM
5.  Client CPU
6.  Client RAM
7.  Client Video Card Performance
8.  Video Software Performance

But which of these are most important?

Unless you have an extremely old or extremely busy network, you can pretty much completely ignore #1.  Gigabit is overkill, 10/100 is plenty, even wireless G is more than enough.

Usb 2.0 supports speeds up to 450 MB/s, so unless you are supporting a lot of simultaneous playbacks, you should be ok with usb 2.0.  You'd be better off with gigabit networked hard drives, though.  Optical SAN storage would be complete overkill.

Server CPU gets more important the more simultaneous playbacks you want to support.  With only one or two playbacks happening simultaneously a decently fast processor on your server is plenty.

Server RAM is not terribly important.  All you are doing is sharing files.

Client CPU is important.  You are never going to get good playback out of an ancient 400 Mhz Pentium III.  I know, I've tried, lol.  You really need something up around 1.8 to 2 Ghz.  My laptop has dual core 32 bit Athlon running at 1.6 Ghz and it can cope pretty well.  My client at 3.0 Ghz is fine, but my work laptop with a dual Intel core at 1.8 GHz and 3.0 GB of RAM struggles.  It's also using VLC though, not Totem.

Client RAM is not terribly important, not if all you are doing is watching movies.  It's important on my work laptop for other reasons.  But I've never seen any of my computers, server (512 MB, client (512 MB), laptop (1 GB) or work laptop (3 GB) ever gated by RAM.

Video card performance is more important, but a decent video card properly configured (no easy task in ubuntu unfortunately) is fine.

And that brings us to video software performance, which is what I've boiled most of my problems down to.  VLC doesn't seem to work as well for me as Totem does.  I was hoping to use VLC across the board because there are versions for both linux and windoze, but I just can't get the smooth playback out of VLC that I can out of Totem.  I haven't really experimented with any other players in Windows.

But since I wrote a client gui to select, play and manage my images using gambas, I think I'll set up a vmware ubuntu image containing my client gui, a mysql and smb clients, and Totem to run the whole client package on windows machines.

Anyway, that's been my experiences so far with this project, please let me know if you have any suggestions, questions or comments.

Thanks

---

