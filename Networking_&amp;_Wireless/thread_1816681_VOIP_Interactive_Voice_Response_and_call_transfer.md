---
title: "VOIP: Interactive Voice Response and call transfer"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by medusa~ on 2011-08-02
[IMG]http://img109.imageshack.us/img109/9917/diagram1x.png[/IMG]

I am complete new to the technical side of VOIP. I know above diagram is not technically correct. But I just did the sketch to request help visually. I want a setup that works like that and oh the cheaper yet not compromising the better, even ekiga or skype can do that pls let me know what is the best option. Thx!

---

### Post by nickleboyblue on 2011-08-02
It is easiest just to use skype.  You could even use Ekiga directly with a voip provider as I do sometimes.  But if that isn't enough customization for you, asterisk allows you to create calling plans, an answering machine, call queues, multiple voicemail boxes, automated tellers, etc.  The downside?  Asterisk is extremely difficult to configure, because unless you get the entire asterisk Linux distribution, you will not have a graphical user interface at all and will be doing all of the configuration from a command line.

I suggest that if you go the Asterisk way, you get a book on the subject before you begin and at least read the section that describes a good hardware setup.  The way I use it is by setting up asterisk on one computer and having all of my other computers "log in" on it.  When a call comes in on either of my numbers, asterisk rings every computer I have at the same time until one of them picks up the call.

As a side note, Asterisk has some very powerful features.  One of my favorites is how it uses bluetooth.  If you know exactly what you are doing, you can run phone calls through bluetooth on old cell phones that don't have cell phone service anymore.  That way you could set up an old cell phone in every room there is an asterisk box and when a call comes in, it can join the group of devices that asterisk rings.

Again, it is easiest to just use Skype or Ekiga, but if you have a month of spare time and the will to learn it, Asterisk can be incredibly rewarding.

---

### Post by medusa~ on 2011-08-03
nickleboyblue, thx for your advise. I would also appreciate detailed howto kind of or steps to go about this setup with ekiga or skype, i prefer non-cumbersome setup and focus on my business. I would appreciate not having to worry about PBX config files. The easier that delivers the required features the better. 

Please at least step by step. I will google more details on the steps. Thx! Anyone?! Thanks in advance to all would be helpers.:D

---

### Post by jonobr on 2011-09-08
Hi

Ive been away from these forums a long time but I had to come back as Im getting back into ubuntu as and getting away from CentOS (to do with a job change) 
I did a search for a problem related to ubuntu and Voip and ran into your post (Update, I notice now the post is from May!).

Im thinking that if your new to this and need to get it working,
you could try (and I hate to steer you from ubuntu) but you could use PBX in a flash- its based on the asterisk engine but doesnt require the configuration of files mentioned by nickleboyblue. [PiaF]("http://pbxinaflash.net/")
There are different variations, but the on I used had CentOS already installed on their.
The installation was really sweet and walks you through the whole thing.

When you finish the install you have a gui where you configure your extensions trunks and so on, There are numerous docs for configuring but its fairly intuitive.

You may have to run a couple of commands but they are not crazy commands.
Configuring your feature set are supported and should be easy

One word on codecs - you mention mobile and GSM
Your phones if they are GSM phones may need to use an AMR codec
This is a licensed codec which will be required on the PBX (asterisk) server.

Piaf as well as other variants, dont include the AMR codec as there are royalty payments associated.
I ran into this issue where they two endpoints could do AMR however, the asterisk engine wanted AMR to transcode the RTP stream and would reject all calls.

I tried using direct media on the PiAF but no joy, I could not get it to work,.

My new job only requires me to use a system that will allow test calls, so im using openser for Ubuntu as this should **cough cough** only proxy and not require transcoding in the middle

Anyhow, I recommend you do a bit of reading on PiAF, or other variants (freepbx,Incredible PBX etc) and see if they are right for you.

One last note, getting to know wireshark for tracing voip is in your future. I would recommend you become familiar with that and how sip works as you are going to be looking at packets sometime 

Good Luck!!

---

### Post by WilsonLast on 2012-05-02
I also search for options for creating a DTMF IVR system, possibly using Asterisk. I tend to choose the solution offered by Ozeki VoIP SIP SDK: voip-sip-sdk.com/p_270-winforms-dtmf-ivr-voip.html

It seems to me quite flexible. I am in the middle of testing and searching for the proper solution...

BR

---

