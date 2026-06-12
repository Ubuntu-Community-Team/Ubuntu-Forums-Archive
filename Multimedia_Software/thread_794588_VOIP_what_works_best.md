---
title: "VOIP: what works best?"
date: 2008-05-14
forum: Multimedia Software
---

### Post by grashdur on 2008-05-14
What would happen if someone very computer literate, but by no means an expert or programmer, tried installing and using six different VOIP setups in Ubuntu? Well, I&#8217;m the guinea pig, and below are the results. 

My intent was to find something that &#8220;just works,&#8221; that allows calls from PC to phone, phone to PC, and PC to PC, and that allows account portability by running on a Windows computer as well as Ubuntu. So here it goes:

**[Note: An updated summary of my own conclusions so far is in post #15 on page 2 of this thread]**

Xlite program using CallCentric.com:
I downloaded a tarball of Xlite 3.0 from counterpath.com, and installed and tried to configure it for CallCentric.com. Though it looked at first like it was working well, after testing it a while I found I had troublesome sound problems. And the phonebook does not not work. CallCentric (the SIP provider) looks pretty good: professional, 2 cents per minute in the US & very low international rates, fax reception and voicemail available at no extra charge, can take over my phone# from Skype, outgoing caller ID. Other Pluses: Great customer service. Downside: To call people on other SIP services you have to enter an unwieldy string of numbers, like **275*6731234567, instead of an SIP address like [email]joe@ekiga.net[/email]. (Xlite is not listed in the poll above since I just added this info after posting and I don't know how to modify a poll after posting.)

Gizmo5: 
On Ubuntu: It&#8217;s not in the repositories, but its .deb file can be downloaded from Gizmo5.com directly. It works just fine, but it won&#8217;t default to using a USB headset &#8212; you have to set it manually each time you plug in (and also lower the output volume level each time, in my case to about &#8220;70&#8221;).
On Windows: Version 4.0.2 won&#8217;t start up -- it just gets stuck at the stage where it says &#8220;Authenticating...&#8221; Version 3.1.2.291 for Windows seems to work just fine, except that my USB headset doesn&#8217;t always work. It seems to work if I uncheck the box in Edit > Options > Audio for &#8220;Automatic Gain Control.&#8221; Sometimes it still won&#8217;t work, unless I recheck that same box, exit from that menu, then come back in to uncheck it again. 
General Pluses: It can call my T-Mobile cellphone for free; outgoing caller-ID is available for a small charge.
General Downsides: Lots of things in the program and on the Gizmo5 website are rather clunky. On the Gizmo5 Forums I read lots of horror stories from people who used to be satisfied with it but are now finding that it doesn&#8217;t work well, and that they never get any response from customer service -- neither directly nor on the Forums. Also, voicemails disappear into your email box, with no notification unless you pay extra for SMS messages. And the program won&#8217;t install on Hardy Heron. 

Skype: 
On Ubuntu: Doesn&#8217;t work well with my headset on Ubuntu (a Skype-certified USB headset, supported by Ubuntu): I have to set Options > Sound Devices > Sound In to &#8220;[USB headset] (hw:default,0)&#8221; and set Sound Out to &#8220;[USB headset] (plughw:default,0)&#8221; while unchecking the box for &#8220;Allow Skype to automatically adjust my mixer levels. Even then, there&#8217;s no volume control and it&#8217;s stuck on a pretty loud setting. Usually there&#8217;s no ring for an incoming call.  
General pluses: Skype is pretty reliable, and the program has a great, easy-to-use interface &#8212; but the Linux version is not as good as the Windows version
General downsides: *No customer service / not much help comes from the user Forums  *People can hack in and change your name (probably applies only to people with SkypePro, as someone is probably hijacking the account to make free calls within the US &#8212; changing the password doesn&#8217;t resolve this)  *Voicemails are recorded in a format that no other program can access  *No outbound caller ID  *It&#8217;s a closed network, so people with SIP softphones can&#8217;t reach you in Skype.  *It won&#8217;t install on Hardy Heron (at least during my brief try of HH).

Twinkle: 
On Ubuntu: A fairly impressive program, except that it has no volume control, and it won&#8217;t respond to Ubuntu&#8217;s master volume control. So the volume is stuck at a fairly high level. I set it up with the SIP provider CallCentric.com.  
On Windows: There is no Twinkle program available. Windows programs that are compatible with CallCentric won&#8217;t run on my PC (in many cases because they&#8217;re not compatible with my ZoneAlarm Firewall &#8212; ZoneAlarm does not recognize that these programs are present and thus does not give them access to the internet). 

Ekiga: 
On Ubuntu: It works well with my USB headset. No problems.   
On Windows: The program can&#8217;t reach its network, even with ZoneAlarm shut down.  
General Downsides: *No phone-to-PC calling available  *Not so user-friendly.

WengoPhone: 
On Ubuntu: Don&#8217;t download it directly from wengophone.com, as it won&#8217;t install due to dependencies. It&#8217;s now in the Ubuntu repositories, and that package installs fine. But the service tends to drop calls, or fails to connect. There&#8217;s no volume control, though the volume is stuck at a relatively comfortable level for most calls.  
On Windows: The program cannot connect to its network, even if I shut down ZoneAlarm.  
Pluses Overall: A very polished, well-designed interface, even better than Skype.
Downsides Overall: Voicemail and phone-to-PC calling are not yet available. 

Conclusion: I probably still won't do much VOIP on Ubuntu. But when I do, I'll use Gizmo5, Twinkle with CallCentric, or Skype, in that order of preference. If and when CallCentric and the WengoPhone program run well together on Ubuntu, I'll use that. 

May this be of benefit. I welcome everyone else&#8217;s experience and feedback on this thread.

---

### Post by Gus_T_Reer on 2008-05-16
Up to this point in time I've only tried Ekiga, Wengophone and linphone.

My config: Hardy 386 desktop, no firewall, behind NAT router.

I've found Ekiga (ex gnomeeting) is good enough for the job but I get choppy video and the app takes about a decade to load. I've seen a bug on launchpad stating that Ekiga would only load thru sudo. It may be the case but I have a suspicion that the bug reporter was/is suffering the same protacted load time as me. It really is that slow to load. I believe version 3 is in the pipeline and I can't wait for it's general release.

I really like the interface for the Wengophone, the video is a lot smoother for me and it allows text chat as well. I think it is using Gaim/Pidgin code to do that so it's quite slick imho. I do have a slight problem with volume levels which seem too low, I have to really turn up the system volume to hear anything properly which of course makes other apps far too loud. There are 2 very small sliders at the bottom left of the app window, one for sound output and one for mic input. I'm led to believe that the app can be used with other sip providers since version 2.1. Unfortunately development seemed to stop around the end of 2007, perhaps due to money running out. The mods on the forum also seemed to disappear about the same time and the forum is now just a X-rated advertising board. Shame. However, things may be running again as one of the original funding partners MBDSYS appears to have picked up the development baton. According to the wiki they are going to rebrand it as Qutecom.

I've just got linphone working with my Ekiga account. I was trying all day yesterday without success but I've booted up this morning and for some reason known only to itself it's working with the same settings I left it with last night. Odd. I notice that the video is very smooth but peculiarly seems to be zoomed-in compared to either Ekiga or Wengophone.

One thing that I'm very sketchy on at the moment is which sip providers allow calls from other sip networks. Ideally with open standards there shouldn't be barriers but skype for instance uses proprietary protocols so I don't think the open sourced apps can contact skype users. If I'm wrong then I'll happily be corrected.

GTR

---

### Post by grashdur on 2008-05-18
@ Gus T Reer: I also feel WengoPhone is the best of all the interfaces. I tried setting it up for the SIP provider CallCentric: It worked well except for sound problems -- no sound out, or no sound in/out, depending whom you're calling. It was because there was no way to disable certain codecs in WengoPhone that interfered with CallCentric's setup. Hopefully these issues can be addressed over time. 

As far as I know, Skype is the only VOIP provider with a closed network. I think the reason why it's hard to figure out which ones are open is that each provider wants you to sign up your friends with them, so they bury their SIP in/out dialling instructions in hard-to-find parts of their websites. But I can specifically verify that the following SIP providers are interoperable: CallCentric, Gizmo5, Ekiga, Wengo.

---

### Post by Ripfox on 2008-05-18
Gizmo ftw. Cheap, reliable, easy to use. Many good features on the web like voicemail to email ect. Big fan here!

---

### Post by manolomanolo on 2008-07-01
Need help using Linphone with my VoipCheap account.
Most of the tutorials I found refer to configurations of that kind
[http://web.ist.utl.pt/jmfv/VOIPBUSTER_Linux.html](http://web.ist.utl.pt/jmfv/VOIPBUSTER_Linux.html)
the only difference is placing sip.vopicheap.com instead of sip.voipstunt.com

But it doesn't seem to be sufficient, maybe because the last Linphone version has changed respect to the old one. Using Linphone 2.1.1 on Ubuntu 8.04 on Asus F3Ja laptop.

Any of you succeded or have the same problems?
Thanks.

---

### Post by Gus_T_Reer on 2008-07-02
Hi manolomanolo,

I can't help you from a technical angle to isolate the problem but I can provide you with my settings that worked for my ekiga account.
Like I said in my original post I couldn't get linphone working either even though I was sure I was entering the correct settings. It was only after a machine shutdown and startup that it kicked into life.
Anyway I'm using linphone 2.0.1 and here's my settings for ekiga, I think you may just need to substitute in your corresponding voipcheap settings:

Sip address: sip:500@ekiga.net
Proxy to use: sip:ekiga.net
Use this STUN server: stun.ekiga.net
RTP port for audio: 7078
Jitter compensation: 60 milliseconds
Playback sound device: ALSA:default device
Capture sound device: ALSA:default device
Recording source: micro
Ring sound device: ALSA:default device
Enable echo-canceller: on
SIP port: 5060
Identity SIP address: [email]xxxxxx@ekiga.net[/email] (my ekiga logon)
Remote services: [email]xxxxxx@ekiga.net[/email] (my ekiga logon again)
Download bandwidth: 513kbits/s
Upload bandwidth: 514kbits/s
_Audio codecs_: 
Name  Rate(Hz) Status  Min bitrate(kbits/s)
speex 16000    Enabled 28.00
speex  8000    Enabled  8.00
PCMU   8000    Enabled 64.00
GSM    8000    Enabled 13.50
PCMA   8000    Enabled 64.00
_Video codecs_:
Name      Rate(Hz) Status  Min bitrate(kbits/s)
theora    90000    Enabled 433.00
H263-1998 90000    Enabled 433.00
MP4V-ES   90000    Enabled 433.00
x-snow    90000    Enabled 433.00

I don't have any other settings turned on or specified.

I hope you find your solution. Good luck.

GTR

---

### Post by mobilediesel on 2008-07-22
> **Ripfox said:**
> Gizmo ftw. Cheap, reliable, easy to use. Many good features on the web like voicemail to email ect. Big fan here!

Gizmo **was** great. Now it wont work and support is non-existent. :confused:

---

### Post by Zeotronic on 2008-08-06
I think Ekiga is a masterpiece of VOIP myself, but judging from the numbers, I'm the only one. I admit, my experience with the others is limited, but if it ain't broke...

---

### Post by izak on 2008-10-07
So is it possible to set up Ekiga to work with callcentric? What exacly must the settings be?

---

### Post by Steve1961 on 2008-10-07
Ekiga with sipgate is pretty good, but I've found that the sound quality is better with skype.

---

### Post by grashdur on 2008-10-07
Ekiga for Callcentric is not something I've tried. And Ekiga is not one of the programs that Callcentric says will work with their service. But if you want to try setting it up, the first place I'd look is at the instructions on Callcentric's website for setting it up on Twinkle. You might also perhaps glance at their instructions for other programs, such as X-Lite, in case there might be any other settings that might be relevant for Ekiga. 

If you do get it to work, please post how you did it on this thread so others will benefit.

---

### Post by zerubbabel on 2009-06-30
Gizmo5 is working fine for me (9.04) for voice and text, but it won't send or receive files. The transfer always cancels immediately after the recipient accepts the transfer. Has anyone else experienced this and found a solution?

---

### Post by zerubbabel on 2009-07-11
Gizmo5 File transfer is working now, after one of their tech support people said he "tweaked the server"...

---

### Post by cknight on 2009-07-20
Sweet review.  Thanks for this.  I'm just entering the VOIP world and this info is really helpful.  I'm off to check out Gizmo5

---

### Post by grashdur on 2009-07-26
My conclusions, updated now: #1 Skype, #2 CallCentric (service) with Twinkle (program), #3 Gizmo5: 

Skype: GOOD: *Portable address book shows up wherever you log in  *Reliable  *Cheap  *Chat/IM is built-in  *Automatic encryption  *Big conference calls possible (up to 24 people)  *Easy to install & set up  BAD: *No customer support available  *Not compatible/interoperable with regular SIP services  *Voicemails are hidden away in a format not accessible to any other program  *Linux version is far inferior to Windows version (e.g. in Linux you have to select the country or write its code *every* time you dial out to a landline number)

CallCentric: Conclusion: GOOD: *Excellent customer service  *Great online login access to account with *lots* of features  *Cheap  *Can take over an existing phone number for call-in service  *Voicemail can be accessed either in the program, or as a listenable, downloadable mp3 file from their website  BAD: *Call quality was inferior to Skype when I compared them last year, especially on international calls -- based on comments I've seen online this may have changed, though  *Softphone options are limited and not very appealing in Linux (only Twinkle works)  {25Jul09}

Gizmo5: Conclusion: GOOD: *Easy to install and set up  *Portable address book shows up wherever you log in  *Can set up IM/chat too   BAD: *No customer support available  *Paid services are still unreliable according to conversations/ratings on the internet  *Interface seems somewhat cluttered compared to Skype

Twinkle: Conclusion: GOOD: *Works well with CallCentric  *Automatically finds and connects with any installed Kontact address book (*very* cool!)  BAD: *No support for dialtone from the keyboard—have to open a special window and press the buttons on it to get dialtones, and this window cannot be called up from any keyboard shortcut  *Main-screen user interface is a bit clunky, cluttered  {25Jul09}

Other Program: SIP Communicator: This little SIP program is still alpha, but it looks really promising—easy to install, very clean and clear user interface. It’s available for Linux, Windows, Macintosh. But it does not yet have enough options available to set up to work properly with a service provider such as CallCentric.

Other Program: QuteCom (formerly WengoPhone): When I downloaded this last year from the Ubuntu repositories, it seemed like a fantastic user interface, perhaps even better than Skype. But I could not set it up for CallCentric because the program could not disable certain sound codecs that got in the way. This month it was not in the repositories, and when I tried to install it two different ways, it failed.

---

### Post by jetpeach on 2009-09-02
i agree that gizmo has really gone downhill for linux - except that now they have a flash version that works right in the browser. i had to change the permissions of flash to allow the microphone to get it to work though, and then there is this crackling sound during the calls that i think is because of the browser based app. it'd be great again though if this gets fixed, though i'd still just prefer if they updated the linux app (it's been 2.5 years since they updated it!!!)

---

### Post by rtalcott on 2009-10-21
Skype is working fine on KK 64 bit...but I cannot get Gizmo and Pulse to work.  Gizmo can peer with Google voice and that's interesting.
rt

---

