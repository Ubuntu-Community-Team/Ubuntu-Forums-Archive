---
title: "Setting up SIP VoIP in Empathy"
date: 2009-12-03
forum: Multimedia Software
---

### Post by freakalad on 2009-12-03
Empathy is now touted as the "official" IM client.

OK? Fine? Not quite sure what's wrong with Pidgin, that I've been using for many years & able to configure & use with numerous protocols (including facebook & skype) quite happily, but I'll play along....

I have a SIP account @ work & with my ISP, and I'd like to connect to said SIP VoIP account & make calls (like SO many windoze users can). 
And, like so many, I can actually multitask, so I can make a call on the head-set while listening to music on the PC speakers.

Has ANYONE actually managed to set up a custom SIP account to a Asterisk/FreeSwitch server, & messed about with the audio, video & codec properties? (what about some logs?)
Where on earth can I find a dial-pad, so that I can actually initiate a call to a POTS/PSTN number, and how on earth do I transfer a call?

Been messing with some other SIP clients, and thus far LinPhone's pretty awesome (small, stable, quality), although it's only draw-back is not being able to transfer calls. 
If only LinPhone could be integrated into Pidgin/Empathy...

---

### Post by richardh on 2009-12-26
I am having problems with VOIP too.
When I use Empathy and try to set up an account that will access SIP, I dont find SIP listed. Somewhere on internet I read a review that extolled Empathy using SIP. But the SIP plugin seems missing from Ubuntu Karmic.

see [https://help.ubuntu.com/community/Empathy](https://help.ubuntu.com/community/Empathy)
At bottom of page is info on how to add SIP functionality.
But I had to reboot OS to get empathy to recognise this. Shouldnt need a reboot.

---

### Post by freakalad on 2010-02-03
Thanks for the info, but I've been down that road before.

I've gotten SIP to register & connect well enough, but that's only for IM.

What is not detailed in the docco is setting up video & voice, which is what I'm after (as demo'd by the link to Jono's page at the bottom of the page).
I need to set up additional settings, such as how to pipe the audio (ALSA and/or PulseAudio), CODEC configutation (G711, uLaw, aLaw, GSM, etc), video, or a keypad for DTFM tones.

At the moment I use about half-a-dozen different clients to cover my comms bases; I'd prefer doing everything (except mail) through a single interface

I'll keep tinkering...

Thanks

---

### Post by martron88 on 2010-04-11
I'm in a similar boat.  I just installed the Lucid Beta and hoped I could get SIP working in empathy.  It seems to register with vbuzzer just fine, however, the option for "Audio Call" is grayed out when choosing SIP contacts.  Also, the "New Call" menu has all options other than google talk grayed out.

I would really like to make/receive calls with empathy.

---

### Post by fukeu2man on 2010-04-18
sudo apt-get install telepathy-sofiasip incoming calls worked liike a charm, have no minutes for my pstn at the moment to check the out going to pstn but i m guess it to will work.

---

### Post by ferossan on 2010-04-20
I'm able to make calls setting my voipdiscount.com account.

Got it to work in Lucid after install telepathy-sofiasip libtelepathy-farsight0 python-tpfarsight.

Just miss be able to add contacts to the SIP account, the option list is greyed out for SIP.

---

### Post by stani on 2010-05-21
> **ferossan said:**
> I'm able to make calls setting my voipdiscount.com account.

Got it to work in Lucid after install telepathy-sofiasip libtelepathy-farsight0 python-tpfarsight.

Can you describe the parameters? I can't get it to work.

---

### Post by martron88 on 2010-05-21
It's tricky.  The way I finally got it to work was to make 2 SIP accounts.  When you create a second account there's a dialog with a bunch more options.  The second account will allow you to start a new call and then you can just dial in the number you want to call.  Once this all works then you can just delete the first bogus account.

---

### Post by ferossan on 2010-05-21
> **stani said:**
> Can you describe the parameters? I can't get it to work.

Well, it did work on Lucid Beta, but now on the final, I can't get it to work again (I did a clean install).
It is lot easier on Ekiga, not very elegant, but at least works fine.

---

### Post by juliobahar on 2010-06-05
Well after relentless weeks of trials I was finally able to connect empathy to my webcalldirect.com sip voip account.

I made a misscall to my handphone, ok. I haven't yet tried to call someone testing audio.

I hope I will give feedback in the coming days.

btw, I can't add contacts to empathy under my SIP account, how can I do that?

---

### Post by ferossan on 2010-06-05
> **juliobahar said:**
> 
I hope I will give feedback in the coming days.

Please do it.

> **juliobahar said:**
> 
btw, I can't add contacts to empathy under my SIP account, how can I do that?
I'm afraid you can't, not at least under SIP. This is another reason why I ended up using Ekiga for SIP.

---

### Post by sanjulive on 2010-07-11
Here's the solution to all of the issues, [https://bugzilla.gnome.org/show_bug.cgi?id=617754](https://bugzilla.gnome.org/show_bug.cgi?id=617754). Requoting from above  for your convenience:

After installing
telepathy-sofiasip and keeping the same settings as mentioned in SOLVED section
of [http://pokazywarka.pl/bug617754/#zdjecie508551](http://pokazywarka.pl/bug617754/#zdjecie508551), I am able to make my voip
account with voipbuster.com work.

In addition to that, I realised you can actually make and receive calls if you
put in the STUN server name, in my case it was stun.voipbuster.com; though I
have to say that, the whole SIP experience with empathy is far not stable.

At least in my case, I have had to restart empathy several times, so that, I
will get the incoming calls from the voipbuster client installed on a windows
pc. Other times, I couldn't hear anything from the caller, sometimes the caller
couldn't hear anything from my side. I am not sure, whether this was due to the
voipbuster client, which cannot be termed as buggy at any rate.

---

### Post by dre12b on 2010-07-20
I also had lots of trouble with SIP on Empathy.  Really it was just one problem - it didn't work at all.

After leaving it be for a couple of months, I installed empathy from the ppa (am now running version 2.30.2) and I'm making and receiving calls from two different SIP providers (sipgate and localphone).  Audio quality is a little shaky, but I think that has to do with latency and tricky NAT on the 3G internet connection I'm using.  I'm guessing that on a solid broadband connection with a public IP, it will work pretty well.

Thanks to whoever sorted this out Empathy side!

FYI I'm also using SFLPhone and keeping an eye out for the release of Blink QT at icanblink.com for Ubuntu SIP clients.  The latter has a lot of promise in particular because it uses ICE for NAT traversal.  I don't proclaim to know how ICE works, but in my experience (using Eyebeam on windows) it gives me great call quality even when I'm behind a NAT firewall without a public IP.

---

### Post by Docaltmed on 2010-10-09
> **dre12b said:**
> FYI I'm also using SFLPhone and keeping an eye out for the release of Blink QT at icanblink.com for Ubuntu SIP clients.  The latter has a lot of promise in particular because it uses ICE for NAT traversal.  I don't proclaim to know how ICE works, but in my experience (using Eyebeam on windows) it gives me great call quality even when I'm behind a NAT firewall without a public IP.

Thanks for the tip. SFLPhone seems to work very well. And it looks like Blink QT has been released, though I haven't downloaded it yet. 

I'm still looking for a a SIP video client, though. Anybody have any ideas?

---

### Post by srf21c on 2011-01-04
I recently figured out how to set up Empathy to work with a Gizmo5/Sipphone VoIP account for use with Google Voice.

As others have noted, ironically the SIP VoiP protocol will not appear as a protocol option in the Empathy "Messaging and VoIP Account => Add..." dialog by default.  The following package must be installed first:

From the command line run:
```
sudo apt-get -y install telepathy-sofiasip
```

Alternately, the same package can be installed via the Ubuntu Software Center by searching for "sofiasip"

Once the package has been installed, a SIP account for Gizmo5/Sipphone can be added by completing the username and password fields and clicking the "Log in" button.

[[IMG]http://img253.imageshack.us/img253/6653/empathyaddvoipaccount.png[/IMG]](http://img253.imageshack.us/i/empathyaddvoipaccount.png/)

Once the VoIP account has been successfully logged into, the Empathy client should now be able to make and receive calls.

One other thing tripped me up at first...the location of the dialpad or keypad is not immediately apparent.  This is a show stopper if you need to press any buttons for DTMF tones during a call, or even accept a Google Voice call when call screening is enabled.  

When an outgoing or ingoing call window is active, look for the sidebar button at the bottom right.  Press to expand the sidebar, then then look for a dropdown menu on the upper right. I believe it defaults to "Audio Input".  If you click this menu, you should see an option for the dialpad.

[[IMG]http://img152.imageshack.us/img152/9137/empathydialpad.png[/IMG]](http://img152.imageshack.us/i/empathydialpad.png/)

---

### Post by rykel on 2011-02-05
Hi guys, I managed to get Empathy to work with [Callcentric]("http://bit.ly/myinum") - FINALLY!

I documented my setup with a screenshot in [my latest blog post]("http://rykel.blogspot.com/2011/02/how-to-set-up-empathy-with-callcentric.html")... hope this helps!

I think that Ubuntu/Empathy should offer a huge list of default major SIP providers in a "Setup SIP" wizard format like what I found in CSipSimple on Android. Having to configure mysterious parameters fails the newbies, I am afraid.

---

### Post by svaens on 2011-02-07
tell ya what! That damn dial-pad is completely hidden and difficult to find. Even when I saw your picture, I had to read very carefully your text to know to look for something that should drop down or pop out .... 

The interface for empathy REALLY needs to be improved.

Speaking of huge lists of SIP providers; 

I've been maintaining instructions on how to use a couple of SIP Phones with my provider (iinet). 

I had written up about empathy (and how it didn't work)
and also twinkle (which did, and does work). 

My empathy write up is here:

[http://whirlpool.net.au/wiki/iinetphone_empathy](http://whirlpool.net.au/wiki/iinetphone_empathy)

I was able, thanks to your tip (@rykel), to get it working yesterday.

---

### Post by pajoohesh on 2011-05-02
For people wondering for webcalldirect in empathy:

using natty after installing telepathy-sofiasip:

username: [email]yourusername@sip.webcalldirect.com[/email]
password: yourpassword
**uncheck** discover the STUN ...
STUN server: leave blank, port: 0
**check** Discover binding
proxy server: sip.webcalldirect.com, port:5060
Mechanism: Auto
Interval: not important, both 0 and 15 works.
authentication username: yourusername
Transport:Auto
**uncheck** Louse Routing

Works perfect.

Have fun,

---

### Post by steve. on 2011-05-15
> **Docaltmed said:**
> I'm still looking for a a SIP video client, though. Anybody have any ideas?

Linphone is a sip client in the repositories that now does video.
They also have clients for other operating systems including Android.
I've made video calls between Ubuntu and Android with accounts on the same VoIP sip provider (Pennytel).

---

### Post by marcantonio on 2011-05-23
> **srf21c said:**
> I One other thing tripped me up at first...the location of the dialpad or keypad is not immediately apparent.  This is a show stopper if you need to press any buttons for DTMF tones during a call, or even accept a Google Voice call when call screening is enabled.  


Wow!  I was starting to think that there was another package I had to install for the keypad.  Thanks!

Marc

---

### Post by cpbl on 2011-06-27
Hello. Setting up SIP VoIP with Empathy was stupidly easy in my case. (freephoneline.ca)
But: how do you make it not auto-answer incoming phone calls?!

(so far, linphone-3 is better featured, though still relatively awful. Haven't tried sflphone yet)

Thanks,
c

---

### Post by MadPoet on 2011-06-29
I managed to set up my VoIP account in Empathy without a problem, but all I can do is make calls; I don't have access to my contact list or my credit information. Any one knows of a way to access this info in Empathy? (or another multi-IM program, I don't care much for Empathy so it doesn't really matter if it's this or another) Thanks!

---

### Post by Magnificent 7 on 2011-08-15
Hello,

I was searching for a way to activate an unused Sipgate VoIP account, mostly to receive incoming calls. Various posts on here were pushing Linphone as the solution, but I decided what the hell, I'll give Empathy a try. Here's what worked for me:

As others have pointed out, Empathy doesn't come with the SIP extensions installed 'out of the box' so you have to run

```
sudo apt-get install telepathy-sofiasip
```

before SIP appears as an option in the 'Edit' > 'Accounts' > 'Add...' dropdown 'Protocol' list. As a belt and braces measure, I closed empathy after installing sofia-sip and killed the telepathy processes before restarting Empathy, but it may not be necessary to do this (?)

Then the settings which worked for me were:

Username: [email]**1234567@sipgate.co.uk**[/email]
Password: ************ *see below

Discover the STUN server automatically: **unchecked**
STUN Server: **stun.sipgate.net** Port: **[color='red']10000[/color]**
Discover binding: **checked**

Proxy options:
Server: **sipgate.co.uk** Port: **5060**

Keep-Alive Options:
Mechanism: **Register**
Interval (seconds): **600**

Miscellaneous Options:
Authentication Username: **1234567**
Transport: **UDP**
Loose routeing: **unchecked**

There's a minor 'gotcha' with the Sipgate password. I couldn't get the account to authenticate at first, and it only worked when I typed the Sipgate password manually into the Empathy password field. Previously I had been selecting and copy/pasting the password from a browser opened onto my Sipgate account, this somehow copies some whitespace at the beginning or end which messes up the password field.

The Empathy SIP client seems quite robust so far, and survives suspend/resume cycles much better than the X-Lite softfone on a WinXP machine I used to use - this had to be restarted at each resume, even though it appeared to be logged in.

With only a few days experience, gripes with Empathy SIP are abundant. How about answering a call; go to top menu bar, click the 'Chat' envelope, pull down to the incoming call in the green envelope. Click on this. A box appears asking whether to accept or reject the call. Well, I've already seen who's calling, via the on-screen alert window. Can't this be a simple click on the alert window, which fades/blurs if any attempt is made to interact with it?

Better still is making a call. Go to top menubar, click on chat icon. Select 'chat' (I usually minimise or close the Contacts List). Go to 'Chat' menu on the Contact List window, select 'New Call'. You're not done yet, now go to the 'Accounts' dropdown, and select your SIP account. Then type the phone number longhand or with one hand while the other is accessing your contacts list on your mobile phone.

What?

It's a real shame, as this clunkiness overlies a very good quality SIP implementation, and I have nothing but praise for the call clarity. The hardware platform, by the way, was a Toshiba Tecra M11-130. If you look elsewhere on the forums, you'll find that although everything works, this machine doesn't play nice with Ubuntu in a ACPI way, due to a buggy DSDT implementation in the BIOS and the requirement to compile a custom kernel with Toshiba optimisations included (which I haven't done yet).

I'll be persisting with Empathy despite all these warts, due to the excellent call quality.

---

### Post by manoynmonic on 2011-09-16
thanks for the tut, finally got empathy talking to my sipgate account.  But no audio once I answer a call!  Anyone else run into this?

---

