---
title: "iPod Nano and Ubuntu"
date: 2009-05-13
forum: Multimedia Software
---

### Post by RealG187 on 2009-05-13
[IMG]http://operation420.net/ipod.jpg[/IMG]

I won an iPod today and am wondering if there is a way I can put songs into it from Linux. I used to use Banshee to put songs on friend's iPods, but Apple "crippled (them) to make it harder for audio software other than iTunes to talk to them" ([Source]("http://www.p2pnet.net/story/13553"))

---

### Post by 3startuna on 2009-05-13
> **RealG187 said:**
> [IMG]http://operation420.net/ipod.jpg[/IMG]

I won an iPod today and am wondering if there is a way I can put songs into it from Linux. I used to use Banshee to put songs on friend's iPods, but Apple "crippled (them) to make it harder for audio software other than iTunes to talk to them" ([Source]("http://www.p2pnet.net/story/13553"))

Congrats!

I just bought an ipod nano the same one you have. 

Amarok works with it, it uploads songs to it and also manages cover flow.

You have to set it up to detect it. Start by downloading "ipod slave" from the synaptic packet manager. 

You can also get gpkpod, download it with all the plugins for video and the lib files to upload songs and pictures, havent tried videos yet

Once you do that open amarok, go to "Configure Amarok" go to "media devices" then select apple Ipod. Here is a link to instructions that worked for me: [http://amarok.kde.org/wiki/Media_Device:IPod](http://amarok.kde.org/wiki/Media_Device:IPod)

Once you get Amarok running well, it will automatically detect and load your ipod when you plug it in.

You can save playlists then drag them to "media devices" and it will automatically transfer the songs to your ipod and save the playlist

---

### Post by RealG187 on 2009-05-13
Now I am using VMWare to run Windows to run iTunes, ironically I won it at a VMWare conference (my friend pointed that out, I didn't even notice!)

So it *does* work on Ubuntu? I already synced with Windows, that woulndn't be an issue would it?

---

### Post by 3startuna on 2009-05-13
Yup confirmed it works with Ubuntu and Amarok. 

I also like amarok more than Itunes it is the BEST audio program I have ever used

---

### Post by RealG187 on 2009-05-14
Yeah, I tried Amarok but it didn't see it.

I wonder if I can use Rhythmbox, that's where my media library is now, is there a way to have Amarok and Rhythmbox use the same library?

---

### Post by 3startuna on 2009-05-14
what is happening with amarok.

Mine did something weird when I first mounted the ipod it would load it but not as a device but as another hard disk or partition. 

Weird

---

### Post by RealG187 on 2009-05-14
All iPods are are flash drives. So that's normal. All iTunes does is copy the song to the removeable media and from what I understand adds the file to an "index" or "playlist" of all the songs.

Which explains when I used Media Monkey on my brother's iPod it said there were no songs, because that iPod used a different syntax or format or something that Media Monkey used. At that time iTunes 7 was needed to write the new format, or that index would be corrupted and it would say there were no songs. This iPod says it needs iTunes 8. Today I tried and it worked with the newer Media Monkey, so I assume the latest media money as of now can write the index of this iPod.

Which explains when the new ones came out and other programs (or older versions of iTunes) couldn't do it is because at the time iTunes 7/8 (depending on which iPod, 7 for my brothers, 8 for mine) could only do it. But I assume Media Monkey, Rhythmbox and Amarok have cought up (not sure about Banshee). And it makes sense that iTunes is always the first app to do this because iPod is made for it.

I also think that before you can use an iPod with anything other than iTunes, you have to use it with iTunes the first time to set it up. Before I used mine I tried Rhythmbox and it didn't work, so then I used iTunes and then Amarok and Rhythmbox after. Today at school I used Media Monkey.

---

### Post by adouglasmhor on 2009-05-15
> **RealG187 said:**
> All iPods are are flash drives. So that's normal. All iTunes does is copy the song to the removeable media and from what I understand adds the file to an "index" or "playlist" of all the songs.

Which explains when I used Media Monkey on my brother's iPod it said there were no songs, because that iPod used a different syntax or format or something that Media Monkey used. At that time iTunes 7 was needed to write the new format, or that index would be corrupted and it would say there were no songs. This iPod says it needs iTunes 8. Today I tried and it worked with the newer Media Monkey, so I assume the latest media money as of now can write the index of this iPod.

Which explains when the new ones came out and other programs (or older versions of iTunes) couldn't do it is because at the time iTunes 7/8 (depending on which iPod, 7 for my brothers, 8 for mine) could only do it. But I assume Media Monkey, Rhythmbox and Amarok have cought up (not sure about Banshee). And it makes sense that iTunes is always the first app to do this because iPod is made for it.

I also think that before you can use an iPod with anything other than iTunes, you have to use it with iTunes the first time to set it up. Before I used mine I tried Rhythmbox and it didn't work, so then I used iTunes and then Amarok and Rhythmbox after. Today at school I used Media Monkey.


I used my GFs Nano with Hipo iPod management tool without ever using Itunes and never had a problem. [http://projects.gnome.org/hipo/](http://projects.gnome.org/hipo/)

---

### Post by RealG187 on 2009-05-15
I wonder can you use the iPod touch/iPhone with Ubuntu?

---

### Post by AddictedGamer on 2009-05-15
I wonder that myself I have a iPod Touch and try to run iTunes though Wine but I can't mount it

Plus for Amarok it only shows (K)ubuntu
does that mean it works on Ubuntu?

---

### Post by Drejcek on 2009-05-16
I have iPod nano too. 
First I upload songs on Windows with iTunse. It's kind a cool because you can get all covers.
Later I tried it with Rhythmbox and it works too but it deleted all the covers. Now I'm using iTunse but it's very stupid for listenig music. Well I didn't try to clean iPod and upload songs only from Rhythmbox.

Maybe I'll do that some time;)

---

### Post by 3startuna on 2009-05-16
> **AddictedGamer said:**
> I wonder that myself I have a iPod Touch and try to run iTunes though Wine but I can't mount it

Plus for Amarok it only shows (K)ubuntu
does that mean it works on Ubuntu?

yeah it runs in ubuntu.

Also I just switched the amarok 2 and it looks likt they really changed the interface im not sure if it still works with it but i know with absolute certainty that it works with 1

Im going to be switching back to 1

another cool feature of amarok is that it automatically downloads the covers, and puts them on. It plays music from the ipod and does basically everything effortlessly. 

gtkpod is also good.

---

### Post by RealG187 on 2009-05-16
Can Amarok put the album art for songs already on there? If it can't what can? I have a bunch of songs with Album art. Can I also remove album art, I have this Album called "Hefty Fine" and it's some good rock-rap, but I don't like the album art (Google image search "bloodhound gang Hefty Fine" to see what I mean")

---

### Post by RealG187 on 2009-05-17
Oh yeah, I can use Rhythmbox to put Music on, but what about Photos and Videos? How can I put those on?

Trying [this]("http://ubuntuforums.org/showthread.php?t=321887") for photos.
EDIT: I get this message ```
/usr/bin/gpixpod: line 2: exec: python2.4: not found

```

---

### Post by 3startuna on 2009-05-17
> **RealG187 said:**
> Can Amarok put the album art for songs already on there? If it can't what can? I have a bunch of songs with Album art. Can I also remove album art, I have this Album called "Hefty Fine" and it's some good rock-rap, but I don't like the album art (Google image search "bloodhound gang Hefty Fine" to see what I mean")

Yup it does that. 

Amarok goes a srep further it will automatically search for the album art download it and apply it

---

### Post by RealG187 on 2009-05-18
I think I used HIPO to change the tag/albumart of a file and then my iPod said there was no songs, I went back into Rhythmbox and added one song, and then it said all my old songs and that one new song was there. Then I deleted the one I added (didn't need it, just put it on to try to fix it) and it's back to normal.

But I know if you use older programs it will "corrupt" the iPod.

---

### Post by fatboab on 2009-05-18
I'd be careful about letting Amarock deal with your album art... All my mp3's have album art embedded, I pluged my ipod in an now half the track on the ipod don't have album art and half of the rest have the wrong album art. Very annoying. Luckily I let Amarock play with a backup copy of all my mp3s, so no real damage done.

Cheers,

-- 
Bob.

---

### Post by 3startuna on 2009-05-18
I tried Amarok 2 last night to upload music to the ipod. It mounts it properly, and transfers songs well, BUT it deleted all my album art so IMHO Amarok 1 is the better program to use

---

### Post by wolfmanjack on 2009-05-18
I use Banshee (from the banshee repos) to manage my iPod Nano, which works excellent, including Album Art etc. Songbird works for managing the music as well but does not support Album Art as of my knowledge.
I never liked Amarok though...

---

### Post by SteveBurt on 2009-05-18
Amarok corrupted all my cover art on a recent iPod (iTunes 8, iPod Classic) - reassigned it all to random albums, since when I won't use it any more.
Fine for music, but not for cover art
Rhythmbox will read the iPod but not write to it.
gPixpod will transfer photos, but you have to do it by hand.

What I want is a tool which does one click syncing of my iPod, including music, cover art and photos.
There is no tool which does this on Linux.
I'm not interested in playing music on my PC.

Nothing on Ubuntu approaches the convenience of iTunes for managing the iPod, I'm afraid. But that's OK - I just use  a Windows machine for the iPod, and my Linux machine for everything else.

---

### Post by RealG187 on 2009-05-19
Amarok has given me album art issues as well. I cannot even get Banshee too see this thing.

I am not sure what versions I have, i'll check tomorrow when I get back to my PC...

---

### Post by 3startuna on 2009-05-19
dude upgrade to Jaunty :)

---

### Post by medicalystoned on 2009-05-19
> **AddictedGamer said:**
> 

Plus for Amarok it only shows (K)ubuntu
does that mean it works on Ubuntu?

It is my understanding that apps are easily transfered and used between distros, ie. kubuntu, ubuntu, mythbuntu, xubuntu, etc.

If this is not the case could somebody please clarify?

---

### Post by SteveBurt on 2009-05-19
Jaunty helps not at all, I'm afraid.

---

### Post by RealG187 on 2009-05-19
I am going to have to do a reinstall on my Laptop anyways, but I feel uncomfortable about upgrading. I know more about 8.10 (which is that, I know 6.10 is Dapper, 7.10 is Edgy, 8,04 is hardy, or was 7.04 Edgy?) than 9.04....

I am downloading the ISO and and am gonna try it out at school first. Can I install VMWare Server 2.0 in 9.04? I know when I had 8.04 I used VMWare Server 1, but then I upgraded to 8.10 it didn't work and I had to upgrade to VMWare Server 2. If I upgrade to 9.04 will VMWare work?

---

### Post by RealG187 on 2009-05-22
> **3startuna said:**
> dude upgrade to Jaunty :)

i did and am regretting every minute of it...

[http://ubuntuforums.org/showthread.php?t=1167432](http://ubuntuforums.org/showthread.php?t=1167432)

---

