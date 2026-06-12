---
title: "help to setup in m3u server on ubuntu and player on network device."
date: 2019-11-25
forum: Multimedia Software
---

### Post by james2k19 on 2019-11-25
Hello everyone, i am new here but i am using ubuntu for few years for now, first ubuntu is so easy to use and adapt by newcomers is so convincing that it made a impression on myself too. used ubuntu on my laptop on early years, then used lubuntu on another low powered laptop, desktop have ubuntu and mint on my main rig, had ubuntu server ,now its redesiged and the ubuntu server is on 18.04.3 LTS running awesome.
i have few services running like emby,pihole,some personal servers,ntp time server,samba, cctv recording,and so on. now i was wondering to run m3u player server. scratching my head now for some time but i am unable  to source any solid ones, found tvheadend but its not easy or what it seems not working what i would want. upon searching i found a link [https://ubuntuforums.org/showthread.php?t=1786955](https://ubuntuforums.org/showthread.php?t=1786955), which kind of what i wanted but instead i want to play the m3u media files content ( not the actual m3u)on remote devices instead of on server itself and that would be video files not only the audio, i have emby running but that only stream local content, and kodi will play but it will create a gui and play on server it self,so no to kodi, can anyone help me in this one please. basically this server will play the content from m3u files and it will push to remote client device as media files and control it without caching on ubuntu server, thank you all in advance &#55357;&#56898;.

---

### Post by TheFu on 2019-11-25
**gnump3**. It is a standalone webserver with some interesting search capabilities.  Clients pull the .m3u playlist file (it is just URLs to the files), then the client plays them.  Normal HTTP access rules apply.  It is not "push".  Password authentication can be required and I suspect a reverse proxy could force https connections, though gnmp3 doesn't support https itself, last time I checked.

Or ... 
Pretty much any music player like **clementine** or amarock or xmms2 can also be used since they all support playlists, just need to provide disk access to the player ... on a LAN, use **NFS**.  Over the internet, you can use **sshfs** (please use ssh-key-based authentication). For audio files, that is almost always fine from a bandwidth standpoint if the "server" has reasonable uplink bandwidth.

Or ....
if you want to be really fancy and forget the .m3u playlists, then most DLNA servers can be used with DLNA controller and DLNA renderers like VLC.  Most are limited to a LAN connection, so getting access over the internet to your media can be accomplish, it just requires some extra steps/knowledge.  It is common for DNLA tools to have server, controller and renderer features all-in-one, but each of these things really is separate, so 1, 2, 3 devices can be involved for any playback needs. A specific example:
* Plex media server as a DLNA server (where the media is stored)
* Android device with BubbleUPnP as a DLNA controller (which selects what is to be played)
* Kodi as a DLNA renderer (where the sound comes out)

I don't think Kodi is a DLNA server. It uses a different protocol, but it can be a controller+renderer or just a renderer.
BubbleUPnP is all three.
Some routers will have DLNA server features. Just plug in a USB drive with media. I wouldn't do this if the router is also the Internet firewall.

---

### Post by james2k19 on 2019-11-26
Thank you so much ,for every detailed steps and information you provided, i will go through one by one and will post up which suits the best for my work, thanks again, have a great day @TheFu.

---

