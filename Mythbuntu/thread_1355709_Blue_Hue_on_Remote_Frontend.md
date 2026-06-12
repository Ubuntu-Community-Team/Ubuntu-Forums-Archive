---
title: "Blue Hue on Remote Frontend"
date: 2009-12-15
forum: Mythbuntu
---

### Post by NertSkull on 2009-12-15
So I have myth tv running fine (including colors) on a computer that acts as the backend and has a frontend on it.  

But I have a frontend in another room that connects to and can play videos/live tv from the backend.  But everything that comes through the front end has a blue hue to it.  How can I fix this?

I've tried going through everything I can find in the frontend menus.  I wouldn't think it is a backend problem, because it looks just fine on the combined front/back end computer. 

And all other colors (outside of mythtv) on the frontend are fine.  Its just the remote mythtv frontend that has this issue.  Any ideas???

---

### Post by NertSkull on 2009-12-15
I should also say, because this may have something to do with it.

My backend/frontend setup is running ubuntu 9.04 with mythtv 0.21.

But my remote frontend is running ubuntu 9.10 where I downloaded from the jaunty repositories the mythtv 0.21 frontend.  So maybe I'm missing something I need.

I did it that way because I couldn't get my video card to work on the new 0.22 mythtv so I left it 9.04.  But my remote frontend is my main computer and I have all my servers and everything set up on 9.10 and don't want to go back to 9.04.  Hopefully I can fix the blue issue with the mythtv 0.21 frontend even though its running on 9.10

thanks!!

---

### Post by klc5555 on 2009-12-15
Depending on the video card/driver on the front end machine, (and whether you have enabled them in the frontend setup) you may have picture controls available to you during the mythfrontend playback (on the dropdown menu keyed to the "m" keyboard shortcut) that will give you control over such things as brightness, contrast, and hue.

---

### Post by NertSkull on 2009-12-15
Yeah I saw that in another post, so I checked the "m" menu while watching live TV but I didn't have those controls.  

I think I have an ok graphics card (NVIDIA 6800).  How do I know if I have enabled it for the frontend to use?   Thanks!

---

### Post by klc5555 on 2009-12-15
> **NertSkull said:**
> Yeah I saw that in another post, so I checked the "m" menu while watching live TV but I didn't have those controls.  

I think I have an ok graphics card (NVIDIA 6800).  How do I know if I have enabled it for the frontend to use?   Thanks!

[http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend)

General Playback (Part 2): Use Xv picture controls
(checkbox) (Default unchecked)  

"If enabled, Xv picture controls (brightness, contrast, etc.) are used during playback. These are independent of the Video4Linux controls used for recording." "The Xv controls may not work properly on some systems, for example some newer Nvidia cards do not support XV picture controls. To see if your machine supports XV picture controls type 'avattr' and look for the variables named XV_BRIGHTNESS, XV_CONTRAST, XV_SATURATION, and XV_HUE. Your graphics card should support picture controls for any of those variables that exist. Unsupported variables will show -1 when attempting to change them." 


What the manual doesn't say is that Xv picture controls on 0.21 simply don't seem to work on _AGP_ Nvidia cards of whatever vintage with whatever drivers. At least I could never get them to work with AGP (6200 and 7300). No problems at all with PCI-e Nvidia cards, nor with the limited integrated graphics (Intel) that I tried them on. So your mileage may vary.

---

### Post by NertSkull on 2009-12-15
Hmmm, well that link didn't work.  But I think its something i've tried already.  In the menu system >> utilities/setup >> setup >> tv settings >> playback  --- then on page 1/9 of playback there is a checkbox for "Enable picture controls" and i've turned that on/off 20 times now and get nothings.

I installed and looked at the "xvattr" for my card (like that quote said) and I get a bunch of XV_BRIGHTNESS and other controls that seem to be working.  My card is a PCIe so that shouldn't be the issue.

I didn't actually find a "Use Xv picture controls" checkbox, but I assume what I found is the same type of thing.

Anything else I can look at or have still missed.

---

### Post by klc5555 on 2009-12-15
Sorry. The stupid forum editing software automatically interpreted part of the link ( "colon" plus "D") as a "grin" emoticon. (And then spelled out "grin" while parsing the link, just to render it hard to spot...).

[http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend)

Lots of good information in the Myth wiki manual, and usually presented in convenient tabular form. Definitely worth a read through.

---

### Post by NertSkull on 2009-12-15
Thats what I figured you were posting to.  I actually have read through that.  Problem is, I have systematically been through every menu available on the front-end and no where is a Use Xv picture controls selection.  And I've tried the "enable picture controls" and it does nothing.

Am I just out of luck.  Is there a command line somehow that I can turn on the live-tv color editing options?

---

### Post by NertSkull on 2009-12-15
Well I have no clue what I did.  I tried reconfiguring the mythtv-common thing, and then I just looked at my video card settings, swear I didn't change anything.  Rebooted, and now I have a change picture menu in mythtv.  So hooray, now to not touch it.

Now I just need to get my audio fixed to remove that blasted high-pitched humming noise, but thats another thread.

Thank you for the help, I appreciate it.

---

### Post by klc5555 on 2009-12-15
Sorry, not that I'm aware of. Since your 6800 is PCI-e, the only further suggestion I can make is to try rolling the proprietary Nvidia driver back from whatever it is in 9.10 to something in the 185.x or 180.x or 173.x range. I don't know whether the XV feature is still supported in the currentmost drivers.

There is also an interesting thread on this in (of all places) the KnoppMyth forum, which may give you further ideas for a solution:

[http://74.125.113.132/search?q=cache:hEavxD6-QHwJ:mysettopbox.tv/phpBB2/viewtopic.php%3Ft%3D20105%26sid%3Dcc2602cb9bd43005012ff08ee080b7a5+%2Bxv+picture+controls+%2Bnvidia+drivers&cd=8&hl=en&ct=clnk&gl=us](http://74.125.113.132/search?q=cache:hEavxD6-QHwJ:mysettopbox.tv/phpBB2/viewtopic.php%3Ft%3D20105%26sid%3Dcc2602cb9bd43005012ff08ee080b7a5+%2Bxv+picture+controls+%2Bnvidia+drivers&cd=8&hl=en&ct=clnk&gl=us)


Ah see that you solved the problem while I was writing. Good job! 

Maybe I should learn how to involve my other eight fingers with the keyboard ...

---

