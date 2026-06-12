---
title: "HTML5 Firefox No Sound"
date: 2015-02-03
forum: Multimedia Software
---

### Post by balia on 2015-02-03
I have no sound in Firefox for any html5 audio tag.
I used the following webpage to test:
[http://hpr.dogphilosophy.net/test](http://hpr.dogphilosophy.net/test)
Supposedly .ogg files are natively supported by Firefox.
But when I click on the ogg file ([http://hpr.dogphilosophy.net/test/ogg.ogg](http://hpr.dogphilosophy.net/test/ogg.ogg)), the file fails to play.
The error console has the following error message: Media resource ... could not be decoded.
I ran this test with no add-ons to make sure that none would interfere with html5
I installed ubuntu-restricted-extras and and gstreamer 1.0 but this didn't solve the problem.

When I run the same test in Web 3.4.1 (another browser provided by ubuntu) everything works fine.
So this seems to be a problem specific to Firefox.

I've search the web for solutions but couldn't find any that applies here.

My setup:
- Ubuntu 12.04 LTS 
- Firefox 35.0

Thank you.

---

### Post by SeijiSensei on 2015-02-03
Try installing gecko-mediaplayer and see if that solves the problem.

---

### Post by monkeybrain20122 on 2015-02-04
Everything works except flac. I think Firefox use gstreamer to decode html5 audio. Check if gstreamer1.0-libav is installed.

---

### Post by balia on 2015-02-04
gstreamer1.0-libav is installed.

As for installing gecko-mediaplayer, why install another media plugin?
Isn't the purpose of html5 to get rid of all the media plugins and play media files directly?

---

### Post by monkeybrain20122 on 2015-02-05
No, gecko-mediaplayer has nothing to do with it. Type about:config in Firefox's url bar, click "I'll be careful, I promise", search  for gstreamer to check if media.gstreamer.enabled is set to true.

---

### Post by monkeybrain20122 on 2015-02-05
It appears that gstreamer is only needed for the mp3 stream. All the other formats still work if the media.gstreamer.enabled string is set to false. So your problem appears to be elsewhere. 

Check if it works with a new Firefox profile. Close Firefox, open the file manager and press ctrl+h or choose  show hidden files, locate the hidden folder .mozilla, rename it to something like .mozilla-bak and now start Firefox, go to the test page and see if it works. To go back to the old profie, close Firefox, delete the folder .mozilla and rename .mozilla-bak back to .mozilla.

Also you may try starting Firefox from the terminal and play the test streams and see if you get any error.

---

### Post by balia on 2015-02-05
Thank you monkeybrain20122, this was very helpful.
I ran firefox from the command line using the default profile and the audio tests worked.
The audio tests were also successful using my regular (shared) profile.

However, normally, I run firefox as a different user (let's call it userwithwebaccess) so that I can give it internet access in iptables.
I have a launcher with:
 gksudo -u userwithwebaccess firefox -P
But when I do so, the audio tests fail even with the default profile provided by Firefox.
I don't think I have permissions problems on the profile directory as all regular browsing works with the exception of html5
The regular profile directory is set to 771.
What is going on here?

---

### Post by monkeybrain20122 on 2015-02-06
So normally it works. It just doesn't work if you run firefox as this restricted user? I guess it would depend on how the profile is set up and what it can access.. I am afraid I can't be of much help here.. But just out of curiosity, does it work if you log into a guest session?

Edited: just tried in guest session. They all work which means you don't need any special permission.

---

### Post by balia on 2015-02-11
I finally resolved the audio html5 issue.
Using the GUI, I went to 
- System / Administration / Users and Groups
- Advanced Settings
- User Privileges
- use audio devices was unchecked so I checked it.
IMPORTANT: This setting takes only effect after rebooting.

Last question:
- Is this the normal behavior when creating a user with a nologin shell?
- How do I change the "use audio devices" from the command line instead of the GUI? Where is the configuration file?

---

### Post by monkeybrain20122 on 2015-02-11
As I said, it works even in guest session so I don't think any special privilege should be involved.

---

### Post by balia on 2015-02-12
Well, there is no audio unless "use audio device" is specifically enabled for the user.
From the command line, this is done by adding the user to the audio group.

If I remove the user from the audio group, the html5 audio fails to play.
if I add the user back in the audio group, the html5 audio files are played.

In this case the audio special privilege seems to be required for any user other than root or guest.
Effectively, guest is not a member of the audio group, so there must be some kind of exception for guest.

---

### Post by Yellow Pasque on 2015-02-12
Have you tried adding the user to the "pulse" group?

---

