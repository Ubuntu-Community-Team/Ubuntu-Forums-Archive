---
title: "Noob:  First Time Hardware questions"
date: 2009-02-22
forum: Mythbuntu
---

### Post by craigmarti on 2009-02-22
Hi all,
      I am a long time Ubuntu user but I am setting up my first Mythbuntu box.  I am building my box from scratch and I have some hardware questions.  I am planning on using this mythbuntu box for all my media.  It will handle all of my audio, television, and movies.  I am hoping that this mythbuntu setup will be able to handle 1080P (Blue Ray DVD Player).  I also listen to a lot of music and I am very picky about quality (more of an audiophile than an videophile).  My plan is to use the processor to process the audio and then send it to my three amplifiers (one 5 channel and two single channel).  Thank you in advance to taking your time to read and reply to my post.

Proposed Motherboard: [ASUS M3N78 PRO AM2+/AM2 NVIDIA GeForce 8300 HDMI ATX AMD Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131320") 

1.  Is it worth the extra cash getting a separate Video Card and bypassing the onboard video card?  If so then what video card do you recommend?

2.  I imagine that the video processing is more memory intensive than the audio processing.  Do you recommend using a separate sound card?  If so then what audio card do you recommend?

3.  Is there any reason why my proposed motherboard is not a good option?  If so then do you have any recommendations?

Again, thanks again for any help. 

Craig

---

### Post by TMcC on 2009-02-22
The motherboard you give should be able to cope with 1080p video, with the VDPAU patches for Mplayer / Myth. 

By far the easiest method to get it to work is to use [http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html).

That is, do a Mythbuntu 8.10 installation - but don't install the NVIDIA driver that comes with Ubuntu; otherwise you'll have some trouble later on.

Then add Mr Avenard's patches repository, and do a "sudo aptitude safe-upgrade".

Note: You'll have to change the mplayer parameters in the video settings if you want to play VDPAU pre-recorded video. I use mplayer_vdpau.sh script as attached, in /usr/local/bin.

All should be OK then; also, make sure you have at least 256MB shared memory for the graphics, I used 512MB on my board.

Then should work OK; I've used a GEFORCE 8200 IGP mini-itx, AM2 4850e. Plays 1080p video at 2-3% CPU.

Note 8200/8300 is a good choice for VC-1 video too.

---

