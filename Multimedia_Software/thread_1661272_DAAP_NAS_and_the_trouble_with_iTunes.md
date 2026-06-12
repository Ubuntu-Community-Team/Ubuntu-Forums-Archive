---
title: "DAAP NAS and the trouble with iTunes"
date: 2011-01-06
forum: Multimedia Software
---

### Post by blackest_knight on 2011-01-06
I bought myself a little Nas just before xmas very cute about the size of a large matchbox with an ethernet port and a usb port 16 meg of ram and a 1 meg flash with an embedded os. 

claims to be able to be able to work as samba server, ftp and media server and bit torrent client. its sold as numerous devices with varying firmware.
thou you might need a hex editor to modify the vendor string in the header.

but it doesn't run linux.

I was most interested in the media server aspect of the device. DAAP is  the protocol used by iTunes trouble is they encrypted it in later versions and now the only programs that can use it are itunes or an xbox or a ps3.

you might find an old version of itunes which might let you connect (oldapps.com )but that doesn't help with my nas server. So I had to take an alternative approach map the smb: share to one ubuntu system (a net book)and run a DAAP server namly firefly and use that as a DAAP Server   
 for my lan. finally DAAP that any DAAP aware system can use.

I even tried xp with iTunes in a VM but it was just not up to playing.
I also had no luck with iTunes in wine  however banshee and rhythmbox work well. 

its best to use a few songs as a start as it takes a while for firefly to catalogue your music.

You don't need to have playlists made or file your songs in any particular order. Till the iTune format of DAAP is known this is as good as it gets. of course its one small step to serve your music collection over the internet.
  
I make this post in the hope it will save time and grief for anyone ese wanting to use DAAP.

---

