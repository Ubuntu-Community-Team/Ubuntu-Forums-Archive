---
title: "Will there be a 0.24.x back port for MythBuntu 12.04 ?"
date: 2012-03-31
forum: Mythbuntu
---

### Post by Henk Poley on 2012-03-31
Easy question, will I be able to run 0.24.x easily if things are broken in MythBuntu 12.04 default MythTV 0.25.

---

### Post by tgm4883 on 2012-03-31
> **Henk Poley said:**
> Easy question, will I be able to run 0.24.x easily if things are broken in MythBuntu 12.04 default MythTV 0.25.

Not sure where to start.

1) You can't backport something into the development version of the distro. There is nothing to backport from (backporting generally means you are taking the newer software version from the development version of the distro and making it available to previous releases)

2) As 12.04 will ship with 0.25, you can't really backport an older version (see #1)

3) Early in the dev cycle, we built 0.24 packages for 12.04. These are still available in the Mythbuntu repository ( [https://launchpad.net/~mythbuntu/+archive/0.24?field.series_filter=precise](https://launchpad.net/~mythbuntu/+archive/0.24?field.series_filter=precise) ). You could manually add that repo, install the 0.24 version and then lock the version. Note that there will be no newer 0.24 builds for 12.04.

What are you worried about being broken?

---

### Post by Henk Poley on 2012-03-31
Sorry for using the wrong terminology. 

Currently LiveTV "transitions" are broken in 0.25. I interpret that as meaning you can't change channels, or pause. Then it won't resume on the (new) channel. 

It's probably my faith in humanity that's showing, but such things broken should not happen ~4 weeks before a distro ships your software.

---

### Post by tgm4883 on 2012-03-31
> **Henk Poley said:**
> Sorry for using the wrong terminology. 

Currently LiveTV "transitions" are broken in 0.25. I interpret that as meaning you can't change channels, or pause. Then it won't resume on the (new) channel. 

It's probably my faith in humanity that's showing, but such things broken should not happen ~4 weeks before a distro ships your software.

People still watch live tv?

---

### Post by nickrout on 2012-03-31
> **tgm4883 said:**
> People still watch live tv?

Yes a very strange phenomona!

What the OP doesn't seem to realise is that 0.25 is not yet released but that when it is, that particular bug should be ironed out, and 0.25-release wil be available on 12.04.

---

### Post by bergqvistjl on 2012-04-01
> **tgm4883 said:**
> People still watch live tv?

Yes. Maybe it's different in the US or something but the culture in the UK is to watch it live, and if you like it, record it for posterity/record when you can't watch it live for some reason. Also, given that "Live TV" in MythTV anyway is just opening a recording from the backend as usual, albeit one still being added to, it shouldn't be too different surely?

---

### Post by nickrout on 2012-04-01
> **bergqvistjl said:**
> Yes. Maybe it's different in the US or something but the culture in the UK is to watch it live, and if you like it, record it for posterity/record when you can't watch it live for some reason. Also, given that "Live TV" in MythTV anyway is just opening a recording from the backend as usual, albeit one still being added to, it shouldn't be too different surely?

the philosophy of mythtv is "record what you want to watch, watch it when you want to watch it"

But in case you weren't following the mailing list closely enough:

[http://www.gossamer-threads.com/lists/mythtv/users/510634#510634](http://www.gossamer-threads.com/lists/mythtv/users/510634#510634)

---

### Post by bergqvistjl on 2012-04-01
> **nickrout said:**
> the philosophy of mythtv is "record what you want to watch, watch it when you want to watch it"

But in case you weren't following the mailing list closely enough:

[http://www.gossamer-threads.com/lists/mythtv/users/510634#510634](http://www.gossamer-threads.com/lists/mythtv/users/510634#510634)

Well I want to watch it as its being broadcast live :p The main reason I use MythTV is because its easy to schedule recording, and I like the duplicate detection, still though the LiveTV Player has come across in leaps and bounds, and doesn't slow down as much for me any more. I only have a few niggles concerning MHEG-I interactive stuff, particularly if the MHEG signal is full-screen. Takes the player a minute or two to sort itself out then, sometimes I have to change to the backend to tune the card to another channel though if it gets stuck with Interactive programs :/

---

### Post by nickrout on 2012-04-01
But in case you weren't following the mailing list closely enough:

[http://www.gossamer-threads.com/list.../510634#510634](http://www.gossamer-threads.com/list.../510634#510634)

---

### Post by bergqvistjl on 2012-04-01
> **nickrout said:**
> But in case you weren't following the mailing list closely enough:

[http://www.gossamer-threads.com/list.../510634#510634](http://www.gossamer-threads.com/list.../510634#510634)

What are you getting at?

---

### Post by nickrout on 2012-04-01
> **bergqvistjl said:**
> What are you getting at?

Read the thread, 0.25 is delayed until the liveTV problem is sorted.

---

### Post by bergqvistjl on 2012-04-02
> **nickrout said:**
> Read the thread, 0.25 is delayed until the liveTV problem is sorted.

Ah, I noticed in the release notes that they said they'd improved loading of live TV, which was nice, still its nice to know they're solving it rather than just telling you not to use it or something like that. Looks like they've improved support for MHEG interactive streams too, which should be awesome.

---

### Post by jyavenard on 2012-04-07
> **Henk Poley said:**
> 
Currently LiveTV "transitions" are broken in 0.25. I interpret that as meaning you can't change channels, or pause. Then it won't resume on the (new) channel. 


First, that bug is actively worked on as it's a blocker and what has delayed mythtv release by a week.
Second, this is only for a specific decoder and analog TV only.

I would assume most use digital these days

---

