---
title: "My Samba/MPD/Sonata conundrum"
date: 2012-02-06
forum: Networking &amp; Wireless
---

### Post by griztown on 2012-02-06
Hi all,

I am trying to set up MPD on a server in my basement hooked up to the home intercom so I can play music throughout the house from any computer in the house. Since the computer in the basement is old, I thought I would simply mount my music files from my normal computer upstairs using Samba. This I did but for some reason I can't seem to play them using Sonata and I'm wondering if this is some sort of a permission issue? I'm mounting the files as a guest so perhaps the mpd doesn't have the ability to read the files? Would Samba block that for the mpd user? I can connect to the server and see the list of music files but when I hit play, nothing happens with no error messages.

Thanks

---

### Post by 2F4U on 2012-02-06
How is the network performance when you access the Samba share with other applications, for example when you list directories from a terminal? Did you try other programs to play music, for example Audacious? I've used Audacious myself to play music over a Samba share from my server and I know that, in general, this works.
I don't know Sonata but it may want to create files on the share such as playlists and since you only gave read permission, this may be the problem.

---

### Post by griztown on 2012-02-06
> **2F4U said:**
> How is the network performance when you access the Samba share with other applications, for example when you list directories from a terminal? Did you try other programs to play music, for example Audacious? I've used Audacious myself to play music over a Samba share from my server and I know that, in general, this works.
I don't know Sonata but it may want to create files on the share such as playlists and since you only gave read permission, this may be the problem.

I can definitely play music from the Samba server on the server with MPD so I don't think that's a problem. I would think that if MPD was trying to create files it would do so in the normal MPD directors under /var/lib/mpd/. The share folder on the Samba server is open to sharing to guest. I've played around with the permissions. I think I'll try copying the files in and see if I can play them if they're physically on the MPD server.

---

### Post by griztown on 2012-02-06
Hmmm. I put a file in my /var/lib/mpd/music/ directory. Assigned it the owner mpd and group audio. And it still won't play. Sonata loads it like it's about to play it and then it stops. Bizarre.

---

### Post by griztown on 2012-02-06
I'm not sure if this is helpful but I've set mpd to verbose mode and I see this when I start it up:

```

binding to address for 10.0.0.16
setFsCharset: fs charset is: UTF-8
libFLAC supports OggFLAC, initializing OggFLAC support
reading DB
Avahi: Initializing interface
Avahi: Client changes to state 2
Avahi: Client is RUNNING
Avahi: Registering servie _mpd._tcp/Music Player
Avahi: Service group changed to state 0
Avahi: Service group is UNCOMMITED
opening pid file
daemonized!
writing pid file

```

---

