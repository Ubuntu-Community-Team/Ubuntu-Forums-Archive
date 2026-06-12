---
title: "advice for a newcomer?"
date: 2010-02-27
forum: Mythbuntu
---

### Post by bnhrobotics on 2010-02-27
I recently decided that I want to have a mythbuntu setup. I have been using ubuntu for a while, so I am somewhat familiar with linux.

My current setup includes a desktop which I use for all my personal computing, an old desktop that I am using for an apache server, and maybe a few other things if I get around to it. Both of these are upstairs and wired into ethernet. The TV is downstairs.

My two biggest issues I am having trouble deciding are:

a) Do I put mythbuntu on my server? I dont watch much tv, and I have other computers I could use as my mytbuntu computer. My server and these others are all just rather old desktops. Ill need to get a new graphics card for either computer to output DVI to the HDTV. The HDTV has DVI, S-video and composite inputs. As far as I understand, DVI is the only way I can get HD to the tv. Power efficiency is also a concern. I dont watch much tv, so if I use a separate mythbuntu server, I would only turn it on when I watch a recorded show. Otherwise, it would be on 24/7 if its on my regular server.

b) The other concern is what TV tuner to get. I like the idea of a well supported tuner like the HDhomerun. I was thinking of getting the one with only 1 tuner because its cheaper and I can't see myself needing to tune 2 shows at once considering how little I watch tv. The issue with this is that Ill have to go wireless to get it downstairs. Could this cause a problem if wireless quality is variable? The other option would be the Hauppauge 1600. I could just connect it downstairs to the cable and not have to worry about transmitting the TV over wireless to the network. Plus, I would have a remote.

Can anyone weigh in on this with their experiences and advice? Thanks

Bryan

---

### Post by nickrout on 2010-02-27
If you don't watch much TV then I wonder why you want mythtv?

Anyway, best use is a separate backend and frontend. Backend has tuner and lots of disk space. It can be anywhere you have a lan connection.

Frontend can be small quiet and close to the TV. Ideally with an nvidia 8xxx or 9xxx or 2xx card with vdpau support. If you have vdpau, you can use an older PC as the cpu won't be doing much.

---

### Post by bnhrobotics on 2010-02-27
Thanks for your reply.

I only have 1 TV and my server does not have a lot of disk space, nor is very powerful. For that reason, I am leaning towards having front end and back end in the same machine.

I don't want to buy a DVR. I feel like this would be more rewarding, and would be worthwhile if one day I decided to expand my network and get another TV.

There is a series called "Life" coming up next month on Discovery. I wanted to record it. I figured that I would end up recording some other things as well. Anyway, how are the video files saved? Could I migrate them from one backend to another if I needed?

My router is being very flaky right now, and there is a combo deal on a router and the 1 tuner HDhomerun on newegg. I may go with that.

edit:
Also, my HDTV which I just inherited has DVI input, s-video and some sort of component. I know nothing about TV's. I assumed to get HD, I would need to go with DVI. As far as I know, s-video would not be HD, correct? For that reason I think I need to get a DVI video card for my box.

---

### Post by nickrout on 2010-02-28
dvi would indeed be your best bet. I reiterate an nvidia card that is capable of vdpau is what you want. 

How do you get your TV? Are you in the US or what? (probably you are if you are buying on newegg). 

Cable? Over the Air (OTA)?

Are your TV channels encrypted? Often they are except for the 'basic' channels. If the channel you want to record is encrypted the only way to go is a STB from your TV company with component out and an HDPVR which takes component out and encodes the signal and then puts it on your computer via a USB connection. 

By the way you seem to be confused between component and composite. composite is a single (usually with the connectors yellow colour coded) video path. It's quality is at the bottom end of the scale. Component has three video signals usually with the cable ends colour coded green blue and red. It will carry hi def just fine, although it is an analogue technology rather than a digital technology.

If you don't know what the terminology I am using means, please have a good look via google and wikipedia for further info.

---

### Post by bnhrobotics on 2010-02-28
Thanks for the advice. I purchased 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814133245](http://www.newegg.com/Product/Product.aspx?Item=N82E16814133245)
Which was on the VDPAU list. I am putting it in an older desktop computer.

The TV came from a friend of my dads who was moving and could not take it with him cross country in his car.

I am in the US. I have a cable company called cox. As far as I know the content is unencrypted, because I just plug the co-ax into the TV and get all of the channels.

My roommate used to use a the dual TV tuner HDhomerun just fine. So I figured I would get the single TV tuner HDhomerun, because I don't really watch enough TV to need two. I ended up buying it on newegg last night because it was in a combo deal with a router. My router is currently going bad, so I wanted to get the deal. If I made a big mistake, let me know and I'll see if I can cancel the order before it ships on Monday.

Thanks for clearing up the component, composite thing. How are the video files stored by mythbuntu? Would it be easy to backup and restore the database?

---

### Post by nickrout on 2010-02-28
tv is usually stored as mpeg ts files under /var/lib/mythtv/recordings.

Backing up the database is dealt with in the wiki, here:

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

---

### Post by bnhrobotics on 2010-03-05
Cool. That looks easy enough. Parts came in, but I won't be able to play with it until next week; probably Friday. Is it possible to selectively back up files, or burn some to a DVD to be read later?

I am excited to start learning about mythbuntu... I think messing with it will increase my knowledge of linux in general too. =)

---

### Post by aovermy on 2010-03-05
Since you're looking to record a show on Discovery, on cable, that means you will need to use QAM on the HDHomeRun. The HDHR supports QAM so if Cox cable delivers unencrypted TV on the Discovery channel and you have a digital cable package, you should be good to go. Your biggest obstacle will probably be finding your channels and mapping them to your listings information. Mythtv has made this less painful than it has in the past. 

Good luck.

---

### Post by aovermy on 2010-03-05
Oh yes, and about the wireless. I have an old house with plaster walls so I also have a wireless network. What I found works well for me is to have a wireless 802.11N router downstairs with all the downstairs computers connected to it via LAN cable. Then I have a 802.11N bridge upstairs with an integrated wired switch and I have the computers upstairs wired to the switch. In that way I limit wireless to just interactions between the bridge and the router and that gives me enough bandwidth to watch HD tv on my downstairs frontend (the backend is upstairs).

---

### Post by nickrout on 2010-03-05
> **bnhrobotics said:**
> Cool. That looks easy enough. Parts came in, but I won't be able to play with it until next week; probably Friday. Is it possible to selectively back up files, or burn some to a DVD to be read later?

I am excited to start learning about mythbuntu... I think messing with it will increase my knowledge of linux in general too. =)

are you talking about backing up the database or tv programmes? TV programmes can be backed up to dvd via mytharchive.

---

### Post by bnhrobotics on 2010-03-12
@nickrout: Great, thats just what I was hoping for.

@aovermy: I am having plenty of trouble finding the channels. Using XP and the supplied HDhomerun software, I only find 10 channels. However, plugging the co-ax cable directly into my tv gives me about 60+. I dont have any cable box. The HDhomerun detects a lot of encrypted channels. What do I to see them?

Using mythbuntu, I have not been able to watch any TV whatsoever. I have been having all sorts of problems with it. I got it installed, it detects, the HDhomerun. I can scan for channels. When I go to "watch tv" it says "Wait" then brings me back to the main screen.

---

### Post by 4dognight on 2010-03-12
> **bnhrobotics said:**
>  I dont have any cable box. The HDhomerun detects a lot of encrypted channels. What do I to see them?



If you are only subscribed to basic cable from Cox, you will not get any encrypted channels. The 10 channels you are seeing is the 10 or so unencrypted Network channels. Sorry to say, but you wont be watching The Discovery channel in HD. You can only get your basic channels in SD, and the few HD network channels.
I have the HDhomerun and only use it for the unencrypted HD channels. I wasn't even aware it could pick up the basic SD channels. I have a PVR500 for them. I also have Cox cable. I subscribe to the extra Digital HD channels, and get them from their STB via firewire.

---

### Post by nickrout on 2010-03-12
> **bnhrobotics said:**
> @nickrout: Great, thats just what I was hoping for.

@aovermy: I am having plenty of trouble finding the channels. Using XP and the supplied HDhomerun software, I only find 10 channels. However, plugging the co-ax cable directly into my tv gives me about 60+. I dont have any cable box. The HDhomerun detects a lot of encrypted channels. What do I to see them?

Using mythbuntu, I have not been able to watch any TV whatsoever. I have been having all sorts of problems with it. I got it installed, it detects, the HDhomerun. I can scan for channels. When I go to "watch tv" it says "Wait" then brings me back to the main screen.

what do your frontend and backend logs say?

---

### Post by bnhrobotics on 2010-03-12
@4dognight
I want to make sure I understand this correctly. My TV sees 75 odd channels. The HDhomerun only sees 10. I assume I have the TV essential package from Cox. I can watch discovery in SD on the TV as is, just by plugging the cable directly from the wall into the TV. However, taking that same cable into the HDHR, I dont get all of those channels. 

So does this mean I CANT get these other channels? If not, then I wasted a bit of money =(. I thought that the HDHR would be able to tune all the of the channels being paid for. Is that not a correct assumption?

@nickrout, I'll let you know when I get a chance to look. 

Thanks for the help

---

### Post by bnhrobotics on 2010-03-12
Ah ok, so I have been doing a bunch more reading up on this. I had no idea that analog was still being transmitted over cable. I thought everything had moved to ATSC. 

So what tuners to Linux people typically use for NTSC? I read that the PVR series by Happauge is no longer available and that the NTSC quality is not very good on the HVR-1600.

I am trying to decide if I should return what I have, get something else, both or scrap it all. Any suggestions?

---

