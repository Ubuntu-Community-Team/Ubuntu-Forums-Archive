---
title: "Setting up my first frontend and have questions"
date: 2010-09-24
forum: Mythbuntu
---

### Post by Meph1st0 on 2010-09-24
I've decided to setup a frontend in my master bedroom and I've purchased an Acer AspireRevo.  I've heard this is a good device as a frontend.

I have a couple questions though about frontends in general.  My backend is a combined frontend/backend with two TV Tuners.  For the sake of simplicity I'm just going to call this one my main box.  I also have an HDHomeRun on my network as well.  At present I'm only using the HDHomeRun tuners for my main box.  Don't ask me why I'm not using the two internal tuners because quite frankly, I don't know.  I know how to set them up, it's cake, I just haven't done it.

But here's the main question.  If my new frontend is configured to use the database in my main box then will it also be able to use the tuners for live tv?  Let's say for example I setup my main box to use the hdhomerun and it's two internal tuners then will my new frontend be able to use all four of those tuners too?   Provided they're available, of course.

Or am I just confused about what a frontend does?  Does a frontend only have access to the recordings (as well as the videos, music and pictures) that are stored on my main box?

I appreciate any responses.

---

### Post by ian dobson on 2010-09-24
Hi,

If you have a remote frontend, you'll be able to use all the resources defined on the backend (Recorded programs, Tuners for LiveTV).

When you start watching LiveTV:-
1) The frontend says to the backend "Please start recording this channel" and tell me what the file name your writing to.
2) After afew seconds the frontand says to the backend "Please send me the recording", and the frontend starts playing it.

So the frontend doesn't attached to the tuners on the backend directly, rather the frontend connects to the backend and it handles all the dirty work.

Note: With liveTV you need to play about with the delays/timeouts abit as there is a lag between the frontend requesting the recording and the file actually being written to the harddisk. This delay is abit higher going through a network.

Regards
Ian Dobson

---

