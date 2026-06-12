---
title: "Certain ac3 Files Will Not Play; Gstreamer?"
date: 2008-11-13
forum: Multimedia Software
---

### Post by spudz1986 on 2008-11-13
I am having some problems playing certain ac3 files. Preface, to this, I am still very new to linux and ubuntu. When I was still in windows, I demuxed from  Against Me!'s We're Never Going Home, the DVD's ac3 files, they always played fine, nothing wrong. When I switched to Ubuntu, there are 18 files total that I demuxed, there are now six of the files that will not play.
After switching over, I copied them from a backup DVD I had, so originally I thought the data might have been corrupted; that is definitely not the case; I had uploaded the files to a torrent site that I am on; I thought, I will just redownload all the clean files. I redownloaded all the files from the torrent site, and the same files will not play. Back in Windows, I had added ape tags to the files in foobar2000, they had always played fine, but I thought maybe the tags had something to do with it, I got rid of all the tags, the same files still would not play; on both the files copied from the dvd and redownloaded. But, under Wine, in foobar2000, I can play all the files absolutely fine, with or without metadata, foobar2000 can still read all the metadata fine, and I can edit the files absolutely fine as well. Same goes for mplayer, I can play all the files absolutely fine in mplayer. But when I hover over them in a window, those same files will not play, while the others will. When I try to import them in rhythmbox, it gives import errors, saying, "The Gstreamer plugins to decode 'application/x-apetag type' files cannnot be found." Although like I said it will import and play the other twelve files with no problem. Even if I remove all the metadata, and try and import them into rhythmbox, rhythmbox again will import all the other files, and will not import the same files, and it gives the same import error, "The Gstreamer plugins to decode 'application/x-apetag type' files cannnot be found." It does this no matter what directory the files were copied from, the DVD or redownloaded, with or without metadata. While I can still play these files in foobar2000 and mplayer. Also, I started having this problem when I originally switched, and that was on Hardy; I am now on Ubuntu Studio Intrepid, and it is doing exactly the same thing. If it is needed my sound card is an Intel ICH6 with STAC9752,53. Thank you all so much!

---

### Post by wolfen69 on 2008-11-13
search synaptic for gstreamer good, gstreamer bad, and gstreamer ugly. you could also download vlc and give that a try.

---

### Post by spudz1986 on 2008-11-13
> **wolfen69 said:**
> search synaptic for gstreamer good, gstreamer bad, and gstreamer ugly. you could also download vlc and give that a try.

i have all the plugins installed; restricted extras, w32, all that ****; all the files will play in vlc; 
like I said the only places where these six files will not play is rythmbox, if I try to hover over them in a window they will not play; everything else plays them fine. so does not that make this a gstreamer issue?

---

