---
title: "stream music with mythweb"
date: 2012-12-12
forum: Mythbuntu
---

### Post by AlecJ on 2012-12-12
Iv'e been trying to stream music from mythweb over the internet, now that I have a fixed ip address from my isp.

Vlc is the only player that I can find that works to play the playlist.m3u file,
But it needs the HTTP authorization to be entered after every track to play the next?
making it really annoying and impossible to use

Amarok also finds the stream but won't play it, but it does however have the "remember login" check box. so working on this maybe the best route?

Banshee, Mplayer and rythmbox  cant find the stream or location

I was able to stream recordings into Vlc but the connection is too slow to watch anything.

Am I missing something?

Would it be possible to share over the net the music folder so as the remote computer could use Rythmbox or whatever?

---

### Post by AlecJ on 2012-12-20
Looking into vsftpd as a solution.

anybody got a working vsftpd.conf file

having no end of hassle trying to setup users and paths for users, beginning to think it don't work on 12.04?

---

### Post by newlinux on 2012-12-21
It's been a long time since I've used mythweb to stream music, so I'm not sure if I can help you with that. But if you are looking into alternatives consider ampache. That's what I use for music streaming with my 80+GB catalog. Works well listening to my music when I'm on the road from Ubuntu or windows, and there are apps that can connect from mobile phones as well.

Another alternative to vsftpd is that you could securely mount remotely using sshfs.

---

