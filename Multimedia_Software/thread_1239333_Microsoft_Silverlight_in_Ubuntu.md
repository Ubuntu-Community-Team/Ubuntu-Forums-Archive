---
title: "Microsoft Silverlight in Ubuntu?"
date: 2009-08-13
forum: Multimedia Software
---

### Post by rocklobster13 on 2009-08-13
I'm in the process of setting up a computer for my TV (htpc). One of the things I wanted it to be able to do is stream soccer games from [www.setanta-i.com]("http://www.setanta-i.com"). I have a subscription but I can't seem to get it to work on Ubuntu yet. It needs two things in order to be able to stream, microsoft silverlight and another program called autobahn. 

Here is where I am at:

Tried to get it to work using Mozilla Firefox. Can't find a silverlight plugin which will work. Did install the moonlight plugin however it doesn't seem to be recognizing it. When you go to the website [www.setanta-i.com]("http://www.setanta-i.com") it tells you whether or not you have the plugin installed, and despite installing moonlight, it is still telling me silverlight is not installed.

Second, tried installing internet explorer through Wine thinking that a microsoft product might have an easier time working with another microsoft product. Did ies4linux and now have IE6 working. Was able to install the autobahn program. Tried to install silverlight through Wine and give me an error "Unable to find a volume for file extraction. Please verify that you have the proper permissions. " What does this mean?

Found some more info on trying to get Silverlight to work through Wine, tried them but none of them seemed to work.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13350&iTestingId=30583](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13350&iTestingId=30583)

Anyone have any ideas of other stuff I can try???

Thanks.

---

### Post by ugriffin on 2009-08-13
Firstly, I suggest you get Firefox for Windows, running on Wine. Firefox should work better than Internet Explorer on Wine.

Silverlight 3 is installable through wine (should detect firefox is installed). In fact, IE doesn't work with Silverlight in Wine. Here's the WineHQ topic but it seems pretty straightforward: FF+Silverlight.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17241](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17241)


EDIT: That error you got was probably a wine error. Did you mess around with the .wine folder? There's a possibility that that folder now belongs to root, and you need to switch the permissions back to normal (running Wine as sudo should not be attempted, in the case that malware for windows actually runs on the thing and destroys your whole root folder).

Tell me the status of your .wine folder. (/home/yourusername/.wine).

EDIT 2: There's a chance that running Wine as sudo might have messed up your .wine too. In any case, check the permissions of the thing.

---

### Post by Copernicus1234 on 2009-08-13
Silverlight, another closed source Windows-Only Microsoft product.... 

It feels very 1999 instead of 2009 to me. The future is on the web based on open standards.

---

### Post by ugriffin on 2009-08-13
> **Copernicus1234 said:**
> Silverlight, another closed source Windows-Only Microsoft product.... 

It feels very 1999 instead of 2009 to me. The future is on the web based on open standards.

And still, that bloody thing is catching on, considering various web-apps are silverlight based.

---

### Post by HappyFeet on 2009-08-13
Install moonlight from synaptic to see if that helps.

---

### Post by AprilWriter on 2009-08-23
Did you ever get SilverLight to work?  The conversation ended.  I have the same problem and would love to see how you solved it.  Thanks!!  :KS

---

### Post by doorknob60 on 2009-08-23
My thing detects Moonlight just fine, but not Autobahn and that's only for Windows or Mac so except for Wine you're outta luck.

---

### Post by odduck on 2009-09-24
> **doorknob60 said:**
> My thing detects Moonlight just fine, but not Autobahn and that's only for Windows or Mac so except for Wine you're outta luck.

Care to elaborate?  I'm trying to do essentially the same thing as the guy in the first post.  It seems that Setanta is no longer requiring Autobahn to be installed in order to access Setanta-i (which must've happened very recently because I know it was needed last week when I tried to sign up for the service).  

Now I've got it working fine on my Windows partition but I'd love to be able to watch some streaming soccer without having to boot into Windows or having to fiddle with Wine.  I installed the moonlight firefox plugin with apt-get but the Setanta-i website still says that Silverlight must be installed.

It's no big deal if I have to use Wine do do this but it'd be cool if I didn't.  Thanks in advance for anyone's help.

---

### Post by bedhead75 on 2009-09-24
Silverlight in Firefox in Wine doesn't work because it still needs a bunch of DirectX stuff.  I think the general consensus is to run Firefox in Windows in Virtualbox and watch it there.  It's the only way I could get Netflix movies to stream.

---

### Post by odduck on 2009-09-24
> **ugriffin said:**
> Firstly, I suggest you get Firefox for Windows, running on Wine. Firefox should work better than Internet Explorer on Wine.

Silverlight 3 is installable through wine (should detect firefox is installed). In fact, IE doesn't work with Silverlight in Wine. Here's the WineHQ topic but it seems pretty straightforward: FF+Silverlight.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17241](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17241)


EDIT: That error you got was probably a wine error. Did you mess around with the .wine folder? There's a possibility that that folder now belongs to root, and you need to switch the permissions back to normal (running Wine as sudo should not be attempted, in the case that malware for windows actually runs on the thing and destroys your whole root folder).

Tell me the status of your .wine folder. (/home/yourusername/.wine).

EDIT 2: There's a chance that running Wine as sudo might have messed up your .wine too. In any case, check the permissions of the thing.

I'm getting the same error message as the OP when trying to install Silverlight through Wine.  I never messed around with the permissions to my .wine folder but what should they look like anyways?  Or could it be some other problem going on here?



Edit: I see.  Well that stinks but I've been meaning to figure out Virtualbox anyways so now this just gives me more incentive.  Thanks for the heads up.

---

### Post by jarrah-95 on 2009-10-04
to install moonlight just go to the microsoft silver light page in linux and try to download it it goes straght to the moonlight page

---

### Post by gilk on 2009-10-05
Sorry, maybe by now, things have changed with silverlight/moonlight and I just installed it from
[http://go-mono.com/moonlight/](http://go-mono.com/moonlight/)
and actually it works.
my problem is now the GNUME MPlayer that stops with out streaming the media....

any idea?

---

### Post by randomAccess on 2009-11-25
Actually SL worked for me until I removed Mono 1.9 and installed the version from this site (x64) and now SL doesn't work. Anyone else having the same problem?

PS.prior to this version, Mono SL installation file was 9MB, and now only 900kb.

---

### Post by randomAccess on 2009-11-26
> **randomAccess said:**
> Actually SL worked for me until I removed Mono 1.9 and installed the version from this site (x64) and now SL doesn't work. Anyone else having the same problem?

PS.prior to this version, Mono SL installation file was 9MB, and now only 900kb.

it works today after i got another update.

---

### Post by beebooty on 2010-08-11
oh, hai, maybe too late ;) moonlight works for me, but i have a trouble with Silverlight 3 whit another soccer page lol, [http://www.mlssoccer.com/videos](http://www.mlssoccer.com/videos), the message says "missed silverlight 3 or something", maybe it works with a future version of moonlight, but a guy posted about to run firefox on virtualbox its relevant to my interest.

---

### Post by Arsic on 2010-08-13
Yeah, I have a similar problem. I want to visit a website that uses Silverlight 4, but Moonlight has only released the equivalent up to Silverlight 3. Is there a beta build I can install?

I found this, but it's still not working. 
[http://www.go-mono.com/moonlight/prerelease.aspx]("http://www.go-mono.com/moonlight/prerelease.aspx")

---

### Post by Chronon on 2010-08-13
Unless Microsoft actively contributes code to Moonlight it will always be playing catch-up.  It takes time to code various features of each version of Silverlight.

---

### Post by C0p3rn1c on 2010-11-12
Silverlight 2.0 installation: 
sudo apt-get install libmoon
sudo apt-get install moonlight-plugin-mozilla
sudo apt-get install ffmpeg

ONLY compatible with silverlight 2.0 video's

---

### Post by dpol on 2011-01-12
Just wondering if anyone has had more success with Moonlight since the last post came out.  I'm running into a similar problem with Fidelity.com that moved their Advanced Chart from Java to Silverlight a week ago or so (brilliant... NOT).  Despite multiple calls and e-mails about reactivating the Java-based Advanced Charts in my Fidelity.com account, no beans.  While continuing my (likely losing) battle with Fidelity, I'd love to know if anyone came up with any type of a fix.  

The new charts work fine through Virtual Box, but that's a work-around, not a fix.

---

### Post by chipchop on 2011-01-27
Moonlight has a release for Silverlight 3 compatibility, last updated Nov 30, 2010.  I have yet to successfully open a Silverlight 3 page with it, but at least it is something.  

My patience has grown thin with the ie7 in wine attempts to load Silverlight.  I haven't played with Virtualbox yet, so that is my next venture.  You can probably find it from the link above, but I'll limit the button clicks for you a little.

[http://www.go-mono.com/moonlight/prerelease.aspx](http://www.go-mono.com/moonlight/prerelease.aspx)

---

