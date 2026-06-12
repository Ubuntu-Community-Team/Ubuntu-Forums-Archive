---
title: "Google Voice Not Working Correctly"
date: 2011-02-17
forum: Networking &amp; Wireless
---

### Post by DarkSideKlyde on 2011-02-17
I recently Installed just Ubuntu 10.10 instead of dual-booting. I can live without my game. I can't, however, live without Google Voice ( I have a prepaid cell for job interviews, I make the rest of my calls on GV). I successfully installed the Google Voice app/plugin or whatever. I can dial out just fine. However, nobody can hear me!! I talk and yell, no matter how close to my screen-embedded mic I am, nobody hears my voice.
I know the mic works as I have used the pre-installed Sound Recorder to record audio (my cam also works via Cheese). When I call someone... they answer and I hear them.. but they don't hear me!! Help as this is my only connection to the "Real World". Why won't Google Voice work from Gmail when my mic works and I can hear the person I called?

DarkSideKlyde

---

### Post by quixote on 2011-02-18
Google voice works like voip, I think.  (Not sure on that.)  On voip, the ring, receiving voice, and sending voice all use different ports.  So, depending which ports you have open, you can get weird situations like no ring, but nice clear conversations, or voice in and no voice out.  The solution is to open whichever port it expects for voice out.

To see whether this is the problem, just take your firewall down completely and see if it works okay then.  If yes, a closed port is the problem.  If no, then it's something else.

I had to troubleshoot all this with my voip (not GVoice), but it was a couple of years ago and I don't remember exactly what I did.  I'd suggest trying to ask which ports GV expects on the Google forums, but I've never got any useful help there.  Still, maybe worth a try.  There's a command, which I'll try to find, or maybe somebody else remembers it!, to get a list of ports being accessed by processes.  I made myself one list before a call, one during, and that was how I finally found the necessary ports.

---

### Post by DarkSideKlyde on 2011-02-20
Thanks for the reply quixote! It does sound like it could be a firewall issue, although, until I read your reply I didn't even realize I have no idea how to access the firewall in Ubuntu. How do I enable or disable it? Looking through my System>Administration menu I could not find the firewall anywhere. Google Voice issue aside, this is something I should know. I guess it just shows my inexperience with Linux. Thanks again.

---

### Post by quixote on 2011-02-20
The firewall is on your router, not in Ubuntu.  (There is something called Firestarter that you can install and run on your computer, but unless you have that, it's not an issue.)

You need to get into the admin section of your router and find out how it's handling ports.  If you have documentation, follow that.  If not, then the commonest method is for the router to be accessed via a browser by typing 192.168.0.1 in the address bar.  It'll have a default login and password that you can probably look up on the company's site.  (Needless to say, keeping it on the default would be a huge security hole since anybody can look that up.) 

Keep at it.  This stuff is hugely tedious, but it's very satisfying when you beat it!

---

### Post by DarkSideKlyde on 2011-02-22
Thanks again quixote for the response. Clarification: For the time being I do not have internet at home. I am using wifi at the local library or Starbucks/McDonald's so I do not have access to the router. I have also tried using a friends smart phone as a wifi hotspot and it still didn't work. I could hear him, but he couldn't hear me. I also tried using a different browser (Chromium) with the same result. It works fine in Windows XP (I had to go back to a dual-boot). I also tried uninstalling and reinstalling the GV plug-in. I am stumped.

As a side note, I looked in to firewalls in Ubuntu and found that it does have a firewall built in that can be accessed from the command line (ufw - uncomplicated firewall) and I installed a GUI for it called gufw. When I opened gufw it showed the firewall as being disabled (I think it's disabled by default by Ubuntu). I entered the following command in the terminal:

sudo ufw disable

and it said the firewall was disabled. I tried GV again with the same result.

Question: Why doesn't Ubuntu need a firewall? I understand the basics of why viruses don't affect Linux like they do Windows, but shouldn't I still be protected through a firewall?

Thanks again.

---

### Post by quixote on 2011-02-23
I wouldn't be surprised if public wifi has the ports normally used in voip closed.  Libraries ought to be a bit more broadminded, but who knows.

Going via your friend's smartphone might be doable once the settings are right.  I have no experience there at all.  If it were me, I'd try searching for "friends-phone-model" "wifi tethering" "voip" "google voice" and see if anything useful comes up.  Usually, it doesn't, which is why I'm only suggesting it as a last resort.

The voip default ports on my system, just as an example, and this is from memory, so probably wrong!, are 5060 Protocol RTP, traffic allowed in and out, and then a whole bunch of really high number ports, 55125 plus-and-minus about fifty also had to be opened to allow the voice-out part to work. The protocol is UDP, also in and out.  The latter ports, I believe, vary a lot depending on your provider.  Google, in your case.

There are ways to scan for ports (which, again, I don't know much about) using System > Administration > Net Tools, and then look under the Port Scan tab.  The problem is that type of scan is also used by crackers trying to break into other people's systems, so it may get you thrown out of Starbucks. ??  I have no idea if it's the sort of thing they monitor or not.  It might be useful, though, if you're trying to troubleshoot the situation with your friend's phone.

Short form: if it's working in Windows, just use that.  If you're worried about malware, install VirtualBox, and install Windows inside that.  As a linux guru once said, it's the only way to run Windows: under supervision. The added advantage is that you can run it virtually inside your Ubuntu, so there's no need to shut down, reboot, etc.

As for why linux doesn't need firewalls: mainly because nobody is writing malware to attack it.  The OS is naturally much more robust than Windows, but if it was being seriously attacked, I'm sure there would be weaknesses. About 2%-5% use Linux which is apparently just too small a target.  Plus, that target has some of the world's wiliest computer geeks on it, who'd probably turn anyone who hacked it inside out.  Just not worth it :mrgreen:

Which doesn't mean you shouldn't be careful.  At public wifi, your biggest problem could be data stealing.  Use encrypted connections whenever you can.  There's a Firefox addon to help with that: [https://www.eff.org/https-everywhere](https://www.eff.org/https-everywhere)

---

### Post by DarkSideKlyde on 2011-03-29
Thank you kindly quixote for all your help attempts. I was content using Ubuntu/XP dual-boot for a while, using XP for Google Voice calls. I just wiped my Windows partition and installed Mint 10, which I am enjoying very much. I was determined to work this problem out and finally came across the solution, given in the following link:

[http://www.google.com/support/forum/p/voice/thread?tid=736cd1781489ed50&hl=en](http://www.google.com/support/forum/p/voice/thread?tid=736cd1781489ed50&hl=en)

The problem is that the GV plugin was taking control of the PulseAudio mic settings and adjusting them as it saw fit. For some reason for GV to work (maybe just on my hardware, I don't know), the left mic channel needs to be turned down to zero. Even with this done, GV resets it as soon as you make a call. A quick edit to the options file (I had to create mine) as described in the above link and it was fixed. I hope this helps someone out as I see there are quite a few views on this post. Thanks again quixote for your help!

---

### Post by quixote on 2011-03-30
Thanks for posting the solution!  That helps everyone.

---

