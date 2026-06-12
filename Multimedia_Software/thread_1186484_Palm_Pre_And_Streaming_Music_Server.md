---
title: "Palm Pre And Streaming Music Server?"
date: 2009-06-13
forum: Multimedia Software
---

### Post by passonno on 2009-06-13
Hi there!

So, I am loving my Pre, but the absolutely killerist app ever for me would be to set up a streaming music server from my home box, and using dyndns and my Pre's browser to access all of my music from anywhere.

Problem is, I have since forgotten what I had learned in the past about setting up a good server, so I am in need of some assistance.

---

### Post by simonlesorcier on 2009-06-14
Yeah! Is it a beauty or what???

I'd also like to see it work with mythtv or mythbuntu. This phone rocks!

---

### Post by corq on 2009-06-17
I did well with "GnuMp3d" - it was pretty easy to set up, gives a browser interface. Once your streaming a directory full of music I think you can locally save that url as a link that would act as a playlist in the future. 

Disclosure: I don't currently have gnump3d set up right now, but this is how it behaved using my Nokia N810.

Also, gPodder - the latest edition sync's podcasts *flawlessly*, in both USB Drive mode, and Media Sync mode on the Pre. 

Highly recommend if you listen to daily podcasts on the go. Until we get an onboard podcast aggregator, gpodder is really sweet.

---

### Post by passonno on 2009-06-18
I have gnump3d set up, but the Pre cannot stream the files for some reason.

---

### Post by afazel on 2009-09-01
I'm using Jinzora2 for this.

---

### Post by EnderTheThird on 2009-10-15
Realizing this thread is still pretty old, I thought I'd chime in anyway.

I've had great luck with Ampache Mobile (from Precentral's Homebrew apps via FileCoaster) and setting up an Ampache server on my media server.  I can stream my music anywhere I get a cell signal and it uses a more friendly UI on the Palm itself instead of having to navigate a browser interface.  Check it out if you haven't found a solution yourself yet.

One note is that Ampache Mobile requires Ampache 3.5.1+ to be installed on your media server.  Last I checked, that version isn't available on Jaunty (9.04).  I had no trouble downloading the new version from the Ampache website and running it on my server though.  I also just checked, and the Karmic (9.10) beta that I'm running on my desktop has Ampache 3.5.1 available via apt.  I haven't tried out the repo version, but if/when you upgrade to Karmic, it should save you some hassle to have everything available via apt like that.  

Do some googling for further instructions, because I know you need to do a little extra setup with the Ampache config files to make sure your Pre can connect.  Enjoy!

---

