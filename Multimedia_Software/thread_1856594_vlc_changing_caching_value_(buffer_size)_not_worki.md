---
title: "vlc changing caching value (buffer size) not working"
date: 2011-10-08
forum: Multimedia Software
---

### Post by doogiekd on 2011-10-08
not getting any replies on the vlc forum & thought i'd try here:


dear friends,

i'm having a weird problem with increasing the caching value for audio files over a smb network.
i have increased the caching value for http, file, & smb to 15 seconds(15000 ms) reason: old equipment & slow network
music occasionally stutters while playing and i wanted a large caching size to prevent this.
i have followed the instructions exactly, changing the caching values as instructed in advanced/access modules.

the scenario after changing the values:

i have followed the instructions exactly, changing the caching values as instructed in advanced/access modules.

i connect to the music directory on a remote pc via nautilus file manager via smb.

i right click on the artist folder and select "open with vlc"

i expect a 15 second delay before the music files start playing. instead, the music files start playing instantly. it appears that changing the caching values did not work.

action taken:

i confirmed that the caching sizes were saved correctly.

questions:

am i correct in assuming that after selecting the music folder, the audio should not start playing for the length set in the caching value (15 seconds) because it is buffering for that time?

or does vlc start playing instantly while it buffers for the set cache size?

equipment/os:

vlc 1.1.9
compaq pressario 5000
512mb ram
lubuntu 11.04
lynksys wrt54g router wireless g

notes:
vlc works perfectly when playing video and audio files locally.

---

