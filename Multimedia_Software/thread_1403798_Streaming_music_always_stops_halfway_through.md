---
title: "Streaming music always stops halfway through"
date: 2010-02-10
forum: Multimedia Software
---

### Post by sensory on 2010-02-10
As the title says, whenever I stream music to my Xbox 360, no matter what I use to stream it, it will stop halfway through and only start up again when the next songs begins to play.

So far I've tested this on Twonky Media Server, uShare, and PS3 Media Server and all produce the same results.

Does any one have a solution for this problem? I'm running 9.10 and uShare at the moment.

---

### Post by sensory on 2010-02-11
Bump

---

### Post by ElSlunko on 2010-02-13
Not sure how you got ushare to work with music! I'm actually trying to get it to work with my media as well but have only had success with Videos. I'll post back if I figure it out.

---

### Post by sensory on 2010-02-13
> **ElSlunko said:**
> Not sure how you got ushare to work with music!
Well, "working" is a bit of an overstatement; it can see the files but can't read the tags so the files don't show up as albums, etc. If I could get the music to play all the way through I'd switch to something else, but since none of them work with music for me I'm sticking to uShare because it's nice and fast.

P.S. I used [this guide]("http://nexus172.wordpress.com/2009/04/26/how-to-stream-video-to-your-xbox360-using-ubuntu-ushare/") to help me with uShare. Seems the version in the repositories leaves out a needed option for XBOX users.

---

### Post by sensory on 2010-02-26
Bump

---

### Post by sensory on 2010-02-27
Bump, I'm surprised no one else has had this problem before me. I've tried uShare, Twonky, Fuppes and Rhytmbox and they all play the music, but are silent after 2 minutes of play until the next song starts.

---

### Post by sensory on 2010-03-07
Bump, multiple clean installs of Karmic, works fine in Windows.

---

### Post by aeronutt on 2010-03-13
I have a similar problem with Twonkymedia and PS3 media server over wireless. (Seems to work fine over ethernet.)

My stops are more random than after 2minutes. Sometimes it'll play for 10-20 minutes, then go silent mid song.

Would love to find a fix.

Running 9.10, streaming to XBOX360 via linksys router.

---

### Post by Kirito on 2011-03-19
I have the same problem as the OP, and also with multiple mediaservers (TVMobili, foobar2000(Wine), Mediatomb) on my Xbox360. Have an Emu0404 PCI soundcard, but never had problems on Windows. Weird thing is, I'd expect sound in movies to have the same problem, but watching movies works fine..

Tried changing alsa settings but hasn't helped so far, unfortunately.
Will be testing my on-board sound soon to see if it's somehow related to the card.

Any other suggestions would be appreciated! It's rather annoying to have your music suddenly go silent after only 5 - 30 seconds of the track have passed.

Edit: Excuse me for bumping this old thread. Misread it, thought it was posted in 2011..

---

### Post by epitaph123 on 2011-08-06
I was able to solve the media not being listed for xbox 360:


1. Right click you music folder and select "create link"

2. Cut and paste the link into your "/media folder" (root privileges required)

3. repeat for any other folders you want (videos etc)

4. open terminal and type "sudo gedit /etc/ushare.conf"

5. edit the following line changing the ushare dir:

          # Directories to be shared (space or CSV list).
          # Ex: USHARE_DIR=/dir1,/dir2
          [COLOR="Red"]USHARE_DIR=/media[/COLOR]

6. open system monitor and kill the ushare process (if it is running)

7. in terminal type ushare -x

Now all folders you created a link to are shared with xbox 360



My question is why does my mp3 audio cut out 20 or 30 sec into a song? 

Xbox 360 says still playing and if you leave it sit after another minute or two the music comes back and is still keeping same time line as if it had never stopped.

why does the audio from mp3's only cut in and out? Video works fine, never had a problem with avi

---

