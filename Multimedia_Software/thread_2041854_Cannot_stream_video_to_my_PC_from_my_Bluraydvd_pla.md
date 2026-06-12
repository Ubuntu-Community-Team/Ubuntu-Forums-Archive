---
title: "Cannot stream video to my PC from my Bluray/dvd player..."
date: 2012-08-13
forum: Multimedia Software
---

### Post by Starfleet on 2012-08-13
Hopefully, this is the right place to ask my question. I've searched and searched to see if I can find answers to this on the net and this forum with no joy.

I'm running Ubuntu 12.04LTS. It's great! However, I have encountered a problem with setting up my software to allow streaming video from my Panasonic Bluray DMR-BW780. I have switched on DLNA in the bluray player. I don't want to actually stream bluray video, just ordinary standard def movies and files.

The computer and bluray are networked in my home to my cable router using Develo network plugs, so I'm not using wireless. I can ping my bluray from within Ubuntu using network tools. It shows up in my router obviously if I can ping it. No problems there. I just cannot see my bluray in any of my programs that I try to use to get video up from the bluray to my PC. I'm primarily using VLC to do this. But wherever I look in Ubuntu, I just cannot see the bluray anywhere. According to Windows users, it's easy and just shows up after making some simple configuration changes. In Ubuntu, it's doesn't seem so easy. 

Has anyone ever done this ok before with Linux Ubuntu? If so, can you give me a pointer or two. I'd be very grateful for any help whatsoever. Everything I've tried so far just doesn't work. It must be some sort of configuration problem I guess. Thanks in advance...

PS. I followed all the Panasonic setup instructions in their manual too.

---

### Post by Starfleet on 2012-08-17
No one done this in Ubuntu? Anyone who has had the remotest little bit of success with this and who has anything to say would be gratefully received... I'm pretty ok with most things Linux but this is just not something I've been able to fathom inspite of reading extensively around it.

Thanks in advance

---

### Post by BicyclerBoy on 2012-08-17
DLNA client is what you need.
DLNA is or uses UPnP, this could be disabled in lan.

Coherence client plugin for totem (gnome) used to work well in 11.04, but this is history.

XBMC has a built-in DLNA client (& server).
VLC uses cyberlink dlna client ? plugin.

djmount (uses fuse) could be worth a look..

Install/run upnp-inspector to check out your DLNA network devices.

(djmount & upnp-inspector are both in std repos.)

Your consumer electronic device is likely to impose strict limitations on bitrate/resolution on streamed media.

---

### Post by Starfleet on 2012-08-28
BicyclerBoy, I want to thank you for your help and advice on this. I'm afraid in spite of checking out all the things you suggest and making sure my dlna is loaded correctly and also switched on in my Bluray device, I've been unable to stream video in Ubuntu using any program. VLC or any other program just doesn't work. I've checked and rechecked my router and network settings and I know they are correct. 

I had a customers computer in for repair the other day with Windows 7 on it. As an experiment I connected it up to my network and found that when I opened Media Player 11, it instantly saw my Bluray and showed the library of films available. A quick double click of a film in the library resulted in me being able to watch streamed video immediatly with very high quality sound into the bargain. So that's good I thought!

I'm not a Windows fan, as you may understand by the fact I'm here. But I thought I'd download a new evaluation version of Windows 8. Just to see if it would stream my videos ok. Well, it does. It's fine. 

So I can assume from all this that my Linux Ubuntu program is just unable to meet the challenge because of some configuration error on my part no doubt. But everything appears fine in Ubuntu. My router settings are fine and I cannot see what I am doing wrong. But hey ho. Windows in a way has solved the problem for now. I don't however want to spend money on buying a copy of Windows. The version of Windows 8 runs out in just 3 months then wont work. But at least it has proven my network is ok. 

I'll keep trying, but if anyone does have some basic information on setting up VLC to stream video over my network then do tell please. Thanks again.

---

### Post by evilsoup on 2012-08-28
Have you tried using XBMC?

---

### Post by BicyclerBoy on 2012-08-29
It is very possible that windows is working because:
Windows media player is an approved/licenced software (HDCP) & the windows OS & video/audio drivers are HDCP compliant.

AFAIK Windows (by default) has uPnP enabled & networking is easy/just works.

A good expt would be to try VLC on the windows box or some other FOSS dlna client.

---

### Post by SeijiSensei on 2012-08-29
I only see three options here: [http://en.wikipedia.org/wiki/List_of_UPnP_AV_media_servers_and_clients#Linux](http://en.wikipedia.org/wiki/List_of_UPnP_AV_media_servers_and_clients#Linux)

and also [Plex](http://www.plexapp.com/getplex/index.php).

---

### Post by Starfleet on 2012-08-29
OK...so an update! 

evilsoup, want to thank you for this bit of advice concerning XBMC, and BicyclerBoy too (I had missed this player listed in your previous post). I can now report that I can stream video from my Bluray to my computer without any problem at all. And boy, how slick is XBMC with it's nice shiny looks and various skins.

But it's the functionality that so brilliant. The network auto discover is a blessing. I haven't yet got full control of the program but I'm getting there. I just need to get my head around it a bit more. I've junked any remote thoughts that were creeping into my brain about running windows as a dual boot just to stream video. 

XBMC now makes my computer one of the most powerful tools in the house. I'll be spending hours and hours no doubt configuring and using it.

Thank you, thank you, thank you!! to everyone for your help. I'll be marking this solved.

---

