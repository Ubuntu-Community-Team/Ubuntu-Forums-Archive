---
title: "MythWeb Music Streaming problem."
date: 2012-02-29
forum: Mythbuntu
---

### Post by jmail524 on 2012-02-29
Hi everyone,

I am having trouble playing my music (MP3) collections through MythWeb.  I can see all of my songs and when I click on the little "play" button, it sends "playlist.m3u" to my music player (usually VLC).  When I checked the contents of the "m3u" file everything seemed okay, but VLC refuses to play it.  VLC says "No decoder found for http://???.???.???.???/mythweb/music/stream?i=???".  If I copy the URL in the message to my browser, it allows me to download the MP3 file but it is only 199 bytes in size.  Neither VLC nor MythMusic has any problem playing my MP3s from my Myth server, they just don't seem to work through the web interface.  I have tried a few different players (VLC, Audacious, Winamp and Windows Media Player). I tried searching for a solution but was unsuccessful. The only items I found that sounded close to my problem was on thw MythTV Wiki and talked about linking the /mythweb/music file to where my music is actually stored, but that didn't fix it. I would appreciate any help in this matter.

Thanks.
Brian

Running Mythbuntu 11.10 with all updates.

---

### Post by jmail524 on 2012-03-02
Anybody???

---

### Post by ijumpship on 2012-03-03
Check the permissions of the music files.I would think.

If you have to authenticate or if mythweb is secure then you need to include that directory.I get this problem on the remote machine.

make sure you do this 

[http://httpd.apache.org/docs/2.2/mod/mod_auth_digest.html](http://httpd.apache.org/docs/2.2/mod/mod_auth_digest.html)

[http://httpd.apache.org/docs/2.2/howto/access.html](http://httpd.apache.org/docs/2.2/howto/access.html)

if mythweb is secure.and test it on the machine holding the music,it always play there.

If You put it in a VLC and it appears to load then exit its a permission problem

M3U are playlist and not the individual MP3 files hence it size will be significantly less than the actual mp3 files

Not all Media players can play(parse) the playlist files hence the decoder error.and easy thing to do is open the M3U files with a text edit,you will see a list of the MP3 ,try those in your media player (mainly open source like VLC)

I had a case where the Music Folder had the permissions (owner,mythtv, others)  of  (readwrite,readonly,readonly) but the individual files had permissions of (readwrite,readonly,none). It never Played.Change the permissions and "Bam!"

---

