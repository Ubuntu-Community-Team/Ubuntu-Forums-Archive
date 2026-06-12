---
title: "Media Management"
date: 2011-02-19
forum: Multimedia Software
---

### Post by RandomCake on 2011-02-19
Hi All,

I've got two identical copies of my media library, one is in MP3 format, the other in FLAC, the MP3 lives on my laptop, and the FLAC lives on a NAS.
When I'm on my network I'd like my media player to use the FLAC copy if it's available, the MP3 if not.

I'm thinking a sym link to my MP3 collection, and somehow detecting when the SMB mount point is available, and then change the symbolic link, but how can I detect the SMB server is available?

I currently use Rhythmbox, but if there is a media player that would support swappable media libraries I'd be open to switching!

Thanks in advance for any advice,

RandomCake

---

### Post by kittkatt on 2011-02-19
Not a perfect solution, but you can write a shell script that does the checking and playing.  Something along the lines of

[email]user@user:testScript.sh[/email] mySong.mp3

if(mySong.mp3 exists on the NAS)
  mplayer its file path
else
  mplayer it locally



A more practical solution would be to apply some metadata details (i.e. put in a comment saying NAS or something) to distinguish all the NAS files, then just import the entire NAS music library into your media library application.  Then you can filter out all the songs with NAS as a comment and search from there.

---

### Post by tgalati4 on 2011-02-19
I run freenas on an old Pentium 1, overclocked to 188 Mhz with 4x500GB IDE drives.  It runs uPnP and DAAP shares.  In Rhythmbox the DAAP share just shows up as "freenas"--you can name the DAAP share whatever you want.  So you have your existing Music Library on Rhythmbox with your indexed mp3's but when you are within your network, the freenas DAAP share shows up automatically at the bottom left side.  This in effect gives you 2 libraries on one instance of Rhythmbox.

What kind of NAS are you running?  Can you hack it to run a DAAP server?

---

### Post by RandomCake on 2011-02-19
> **tgalati4 said:**
> I run freenas on an old Pentium 1, overclocked to 188 Mhz with 4x500GB IDE drives.  It runs uPnP and DAAP shares.  In Rhythmbox the DAAP share just shows up as "freenas"--you can name the DAAP share whatever you want.  So you have your existing Music Library on Rhythmbox with your indexed mp3's but when you are within your network, the freenas DAAP share shows up automatically at the bottom left side.  This in effect gives you 2 libraries on one instance of Rhythmbox.

What kind of NAS are you running?  Can you hack it to run a DAAP server?

Sounds likely, it's a Netgear Stora (runs a RedHat variant), it already broadcasts as 'Stora:iTunes', and having looked at at what's running on the back end it seems it's running:

Firefly Media Server: Version svn-1696

I've told it via the config file that I want it to serve Flac files, and it has shown them in its list, but as soon as I ask it to play them it crashes Rhythmbox.
<edit> it crashes the server too </edit>
Luckily Banshee seems to work well with it! From a bit of reading around it seems there is a bug in Firefly's handling of Rythmbox sending a HTTP header twice, so a bug in both, but Firefly should really handle it more gracefully.

---

