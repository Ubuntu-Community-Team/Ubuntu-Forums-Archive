---
title: "Dare I upgrade to 0.25?"
date: 2012-09-01
forum: Mythbuntu
---

### Post by marek_online on 2012-09-01
Hi,

I have a MythTV box (backend/frontend). This is the only TV in the house, so it's important that it stay working. It's currently running Mythbuntu Oneiric and 0.24 + updates from the mythtv repos.

The machine has a blu-ray drive and I'm wondering whether its worth the risk to upgrade to Precise and 0.25 to get to LTS and some working blu-ray disks.

Recordings are on their own partition, as is /home (along with the folders for images, music and videos), but I would prefer not to lose the recordings (a few hundred hours, mainly my wife's).

The machine is:
Intel Core i3-370M 
4GB RAM
NVIDIA GeForce GT425M Graphics
PCTV nanostick for DVB-T2
TeVii usb for DVB-S/S2
1TB external eSATA drive for /var

Am I just asking for trouble trying to upgrade (if it ain't broke....) or do you think it would be safe enough.

Just wondering about people's opinions or experiences upgrading.

---

### Post by GaryP2 on 2012-09-01
I upgraded to .25 from .24-fixes a few weeks ago and am a bit sorry I did so. I want to start trying to use the new HTTP streaming to an Android tablet is the primary reason I upgraded. 
 
I’ve run into to issues that feel like a setback to me: 1.) [PVR analog tuners keep going unresponsive]("http://code.mythtv.org/trac/ticket/10732") within a day until I reboot the backend, and 2.) mythcommflag segfaults occasionally (Failed with exit statue 140) causing some shows to not be commercial flagged. 
 
I don’t plan on going back to .24 at this point because I don’t use the analog tuners very much, but I’m a little concerned that this issue may not be fixed anytime soon (it’s been assigned a bug ticket for four month with little documented progress). You may not run into this issue if you don’t have ivtv analog tuners.
 
Other than that, the backend and frontend has been pretty stable with .25 for me. I’m still on 10.04.4 LTS.

---

### Post by zarthan on 2012-09-01
If you aren't having issues or aren't frustrated by lack of a particular feature I would sit where you are and after all .26 is around the corner. Any upgrade will pose it's own set of challenges and it may take many hours to get everything comfortable again. Don't risk the fall schedule. Just my opinion.

---

### Post by marek_online on 2012-09-01
Thanks for the viewpoints.

Will probably stay where I am for the minute. I don't have any analog tuners (just a DVB-T2 and a DVB-S), but was only the possibility of the blu-ray that was really enticing. That and moving to an LTS release.

I'll mess around with the blu-ray through VLC and command line for the moment I suppose.

Might still need to upgrade to get onto the LTS schedule before I miss the boat in October though...

---

### Post by nickrout on 2012-09-01
> **marek_online said:**
> Thanks for the viewpoints.

Will probably stay where I am for the minute. I don't have any analog tuners (just a DVB-T2 and a DVB-S), but was only the possibility of the blu-ray that was really enticing. That and moving to an LTS release.

I'll mess around with the blu-ray through VLC and command line for the moment I suppose.

Might still need to upgrade to get onto the LTS schedule before I miss the boat in October though...

The bluray support is worth upgrading for.

If I was you I would back up my database and do a fresh install of 12.04.

---

### Post by marek_online on 2012-09-02
> The bluray support is worth upgrading for.

Hmmm. Now I'm back to being tempted. I can't actually find much by way of detail on the support though. Do menus work? 

And how often do you hit on BD+ discs? (I've seen another thread that suggests it really only Fox that use BD+ consistently, but haven't been able to google up much specifics.)

Thanks.

---

### Post by nickrout on 2012-09-02
> **marek_online said:**
> Hmmm. Now I'm back to being tempted. I can't actually find much by way of detail on the support though. Do menus work? 

And how often do you hit on BD+ discs? (I've seen another thread that suggests it really only Fox that use BD+ consistently, but haven't been able to google up much specifics.)

Thanks.

Well to be honest I don't do bluray that much. But for the few I have, the thrill of having it working in linux was a joy. I had a "discussion" in some online forum about whether bluray worked in linux, he was adamant it didn't and never would :)

I probably should have saud "If you do bluray, the upgrade is worth it!"

It doesn't do menus, but you can choose which title to watch.

---

### Post by Pantera116 on 2012-09-02
I am considering upgrading my mythtv setup to 12.04 and 0.25 mythtv.

I have a separate backend and a few frontends.

I am still on 10.04 backend and 11.04 frontends (all 0.24 mythtv)

Is 0.25 mature now? is the ugprade likely to be wortwhile and problem free?

I would put the backend os on a new/clean ssd and then import a current backup of the database and re-map my 4 off storage discs. Anything else needed except the odd proprietary driver?

I understand that 0.25 is supposed to fully support Blu Ray straight from disk. So if i had a Blu Ray drive in my backend could i watch it on either of my fronends?

Could this be a better option than a stand alone player which would only serve one room?

---

### Post by marek_online on 2012-09-02
> But for the few I have, the thrill of having it working in linux was a  joy. I had a "discussion" in some online forum about whether bluray  worked in linux, he was adamant it didn't and never would :smile:

I know the feeling :-) .

No blu-ray collection, so I won't rush into things.

Will probably hold off on the full upgrade until I have time to work through it carefully (had wondered whether a couple of hours on a Sunday afternoon might do the trick - but I'll block off a bit more time for instead...)

---

### Post by nickrout on 2012-09-02
> **Pantera116 said:**
> I am considering upgrading my mythtv setup to 12.04 and 0.25 mythtv.

I have a separate backend and a few frontends.

I am still on 10.04 backend and 11.04 frontends (all 0.24 mythtv)

Is 0.25 mature now? is the ugprade likely to be wortwhile and problem free?

I would put the backend os on a new/clean ssd and then import a current backup of the database and re-map my 4 off storage discs. Anything else needed except the odd proprietary driver?

I understand that 0.25 is supposed to fully support Blu Ray straight from disk. So if i had a Blu Ray drive in my backend could i watch it on either of my fronends?

Could this be a better option than a stand alone player which would only serve one room?

No I think the bluray drive needs to be in the frontend.

However you could rip to the backend and have it available on each frontend.

---

### Post by Pantera116 on 2012-09-03
> No I think the bluray drive needs to be in the frontend.

However you could rip to the backend and have it available on each frontend.


What is required to do the ripping?

Internal mythtv tools or 3rd party applications?

---

### Post by nickrout on 2012-09-03
> **Pantera116 said:**
> What is required to do the ripping?

Internal mythtv tools or 3rd party applications?

makemkv seems the most popular choice on linux. It is not free, but not too expensive either.

It takes the stream on dvd or bluray and repacks it in a mkv container. It does not compress the file, so you end up with a large but high quality file.

You could then use something like handbrake if you want to compress it further, although this will take time and processor power.

---

### Post by Pantera116 on 2012-09-04
Thanks for that nickrout.

What other pros and cons are there regards upgrading to 12.04 and 0.25?

In my case post potential upgrade the os would be on ssd. I could then spin down the storage drives when not in use to reduce power consumption and heat which in turn could extend the life of the drives.

I may also be able to tidy up the channel numbering. The satellite channels are in no paticular order or number grouping. If i could get xml program info working for satellite i could eliminate all the additional regional versions. Freeview channels work fine as does hd recordings of both satellite and terrestial (TBS brand) tuners. I use EIT for freeview.

Reliability wise i get the odd dropped recording. I recently had the backend up for 40 days straight, so not too bad!

---

### Post by nickrout on 2012-09-04
> **Pantera116 said:**
> Thanks for that nickrout.

What other pros and cons are there regards upgrading to 12.04 and 0.25?

In my case post potential upgrade the os would be on ssd. I could then spin down the storage drives when not in use to reduce power consumption and heat which in turn could extend the life of the drives.

I may also be able to tidy up the channel numbering. The satellite channels are in no paticular order or number grouping. If i could get xml program info working for satellite i could eliminate all the additional regional versions. Freeview channels work fine as does hd recordings of both satellite and terrestial (TBS brand) tuners. I use EIT for freeview.

Reliability wise i get the odd dropped recording. I recently had the backend up for 40 days straight, so not too bad!

Upgrading will not change your channel numbers or ordering, all that will remain exactly the same as it it is in the database which you will retain.

Where are you? Mention of "freeview" suggests UK or NZ. If UK use radio times xmltv. If NZ use tv_grab_nz-py. Everyone agrees that EIT is pretty crap.

Advantages? 

*There are not many fixes going into 0.24.

*Channel switching in livetv crosses tuners if needed.

*Http Live Streaming

See the 0.25 release notes in the wiki for more details.

---

### Post by Pantera116 on 2012-09-04
Bit of clarification, iam in the uk.

I accept your point about the current channel details in the database. Good point about few remaining fixes for 0.24

EIT on freeview (8 day epg) used to occasionally stop updating, ok for the last few months on the TBS tuner. 

The satellite gets the astra 2b free to air channels. The channel numbers are the sid codes.see link

 [http://www.lyngsat.com/Eutelsat-28A-and-Astra-1N-2A-2B.html](http://www.lyngsat.com/Eutelsat-28A-and-Astra-1N-2A-2B.html)

I think that there was a issue with 10.04 and xml, So not implemented yet,
should work fine under 12.04.

Hopefully using xml **post upgrade**  i would have a more 'freesat' type channel list.

---

### Post by nickrout on 2012-09-04
You can number your channels however you want. Go to mythweb and go to mythweb/settings/tv/channels. Use whatever numbers you like for channum. Don't forget the "Save" button at the bottom of the page.

---

### Post by Pantera116 on 2012-09-05
I make extensive use of Mythweb but did not relise it could do this.
I will check it out.

If i can define satelite channel numbers i will probably use the fresat numbering but start it from 1000 as the freeview numbering goes from 1 to 728.

Looks like i will have to find a timeslot to do this 12.04/0.25 upgrade.

---

### Post by nickrout on 2012-09-05
> **Pantera116 said:**
> I make extensive use of Mythweb but did not relise it could do this.
I will check it out.

If i can define satelite channel numbers i will probably use the fresat numbering but start it from 1000 as the freeview numbering goes from 1 to 728.

Looks like i will have to find a timeslot to do this 12.04/0.25 upgrade.

I don't know much about what is on freesat and freeview, but if any channels overlap (ie have exactly the same programming all the time) then you can optionally give them the same callsign and channel number and xmltvid then when your life will be simpler.

---

