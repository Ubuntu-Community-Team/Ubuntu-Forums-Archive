---
title: "Installation of 9beta breaks pvr350&amp;500 cards"
date: 2009-04-12
forum: Mythbuntu
---

### Post by MonsterMaxx on 2009-04-12
I installed 9beta on a machine that had a working centos/myth installation.

I was able to get mythbuntu running, the database restored, but never could get the thing to record - card errors. I was able to configure the cards, but they won't work.

So I table the mythubuntu installation for now and boot back into centos, everything is fine. Except when I check for upcoming recordings again there is nothing.
When I check the cards themselves they all probe 'failed to open'


What could cause that? Something in mythbuntu had to have done this.


Not slamming mb, just trying to solve my problem. Actually, I kind of like it. Enough to continue with the install until it's working anyway and give it a real run for a year, like i did with centos.
FYI: verdict on centos/myth is that it's not a great combo, fedora was better

PS: centos/myth install is up to date

---

### Post by MonsterMaxx on 2009-04-13
Allright, now I'm really getting frustrated.

This time I installed 8.1. I did NOT import my existing database, just did a pure clean setup and tried to set a recording.

No joy. Myth will not schedule a recording.

So then I got all medevil on it's azz, did the manual command line stuff to verify functionality.

I can record off all three cards. Recordings play just fine.

I can tune in with one card (in myth) and watch live TV, but 'c' to change to another card doesn't work.

?????

What could I be missing? I have set up myth systems in the past and not had trouble. This hardware is known working (or was until I installed mythbuntu and there have been zero hardware changes.)
I must be missing something. What could it be? Is there something that needs installing in mythbuntu for the PVR350 & 500 which is not preinstalled? Because command line wise the cards are working, just not in myth (the 350 will do live TV, none of the others respond, scheduled recordings don't happen at all.)

---

### Post by MonsterMaxx on 2009-04-13
really? no one has any idea how to solve this? come on, surely someone must know

---

### Post by joshoekstra on 2009-04-14
The stages where it generally goes wrong:
- you cannot install the pacckages
- you didn't configure the database
- you didn't run mythtv-setup where:
- you didn't configure your card
- you didn't configure your listings
- you didn't connect your listings to the cards/ or configured the wrong starting channel. Or:
- your hardware is broken

It seems like quite an accusation, but it's just a list to check.
The first 4 you seem to have done(for each card as well?) The listing and connecting it to each card is where it might go wrong or the starting channel.

So some logs of backend and frontend might be good to post as well as your video-devices.

---

### Post by MonsterMaxx on 2009-04-14
- you cannot install the pacckages
- you didn't configure the database
- you didn't run mythtv-setup where:
- you didn't configure your card
- you didn't configure your listings
- you didn't connect your listings to the cards/ or configured the wrong starting channel. Or:
- your hardware is broken

The first four are absolutely done as is the second half of 6 (starting channel.) I've tested them with the command line and all the cards WILL record and I can playback thru mplayer. All three tested and verified working (also, they have been working under a variety of other distros for years.)

Configure my listings? If you mean set them up on schedules direct and connect thru mythsetup to get the channel linup (where it also sets the first channel.)
It's generated all the channels in the channel editor.


Now, what is 'connect your listings to the cards'??? {that sounds promising}

---

### Post by joshoekstra on 2009-04-14
> **MonsterMaxx said:**
> 
Now, what is 'connect your listings to the cards'??? {that sounds promising}
It's where you make the connection between the listings(in your case from schedules-direct) to a card.
It will look something like:
[MPEG: /dev/videoX] (tuner1) -->(None)
Change this to:
[MPEG: /dev/videoX] (tuner1) -->(Schedules-direct)
That way you connect the data to the devices.
It's just running mythtv-setup and following the numbered steps 1-4(at least) you can also change 5 and 6 if you feel the need.

---

### Post by MonsterMaxx on 2009-04-14
huh? where do I do such a thing? you talking about the 3rd (or is it 4th) setting under mythsetup where we set each tuner to use the channels?

(I've been installing a different distro and can't get to a mythsetup screen at the moment)

Ya, that's been done.

---

### Post by MonsterMaxx on 2009-04-15
I thought I'd had it figured out, got grub fixed up and back into 9beta.

What I was thinking was that I use another drive for storage, mounted as /storage.
I'd created it as root, but hadn't set the permissions so mythtv user could...

So I just tried again and 777 it.

no joy

So I 777 the whole storage drive just to be sure.

no joy.

<--stumped

---

### Post by MonsterMaxx on 2009-04-15
What is so strange about this is that the machine was working fine under Centos, then I installed mythbuntu 9 beta and it's never worked since - even in other distros. Even in the Centos distro that's been working for ages(though I did an update when I logged back in...) Even in brand new installations of other distros.

Everything seems to be working - all tests from the command line pass and I can view live TV in myth, but Myth will not schedule any recordings. It just ignores the save when I tell it to record.

---

### Post by klc5555 on 2009-04-15
> **MonsterMaxx said:**
> What is so strange about this is that the machine was working fine under Centos, then I installed mythbuntu 9 beta and it's never worked since - even in other distros. Even in the Centos distro that's been working for ages(though I did an update when I logged back in...) Even in brand new installations of other distros.

Everything seems to be working - all tests from the command line pass and I can view live TV in myth, but Myth will not schedule any recordings. It just ignores the save when I tell it to record.

A shot in the dark, but was your mythbuntu default desktop user ever added to the "mythtv" group? 

With myth in some other distros (or compiled) everything by default is done either by "root" or by any-and-all other users equally. With mythbuntu, root is kept safely locked away like the crazy old uncle in the attic, and most database functions are done by the "mythtv" user and the "mythtv" group, to which the default desktop user must be added.

---

### Post by MonsterMaxx on 2009-04-15
Interesting, I'll try that next...in fedora. For some reason it's partitioner decided the disk was unreadable, after 4-5 reboots and different tries I'd pushed the wrong button at 4am and...yup, starting over again.

Thanks for the help, will get back to you with results when I can...

---

