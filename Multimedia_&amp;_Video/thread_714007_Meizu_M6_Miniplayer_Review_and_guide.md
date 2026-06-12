---
title: "Meizu M6 Miniplayer Review and guide"
date: 2008-03-03
forum: Multimedia &amp; Video
---

### Post by mooglinux on 2008-03-03
EDIT: 3/6: added more instructions in responce to a question

I have noticed several questions regarding this player floating around and awnsers to various questions about it, beit troubleshooting or compatibility, the awnsers are all scattered over the net, so here i am to condense it al into one handy place.

REVIEW
Meizu is a chinese brand, who makes several mp3 players available here ("here" being a relative term, i will qualify: the US) and the m6 is a nice player with a footprint slightly smaller than a drivers license, built nicel, and available for quite cheap. I purchased mine, the 4gb sp version, from newegg.com for $80 with a mail-in-rebate.

BUILD: the build of this player is nice, with a good solid feel to it, without being too heavy or too light. Unlike the 1st gen ipod nano's, there is no sense of fragility. go ahead and squeeze it, nothings gonna break (*cough* ipod *cough*) The interface is a touch strip on the right side of the screen (you hold it in a horizontal orientation btw) that is sensitive but not overly so. on either side of the strip are the next and previous buttons, and on the top of the strip is the menu button, and on bottom the enter button. on top of the player is the play/pause/power button, and on bottom is the hold switch. 

The buttons have a noticible feedback when pressed, even if you operate it through the cloth of your jeans (why pull it out all the time just to change tracks?) and the touch strip only responds to the touch of flesh, no fingernail or pencil will operate it. on top of that the buttons all sit flush with the face, so there is no need to use the hold switch when placing this in your pocket. 

 its solid. i have dropped it a few times but never from very high or on a very hard surface. i suspect that it would take a rough tumble without much fuss, it certainly wont shatter like an ipod can. so i would agree that it is quite durable, just dont take off the plastic covering! with that on, nothing in the world will scratch it. i was smart enough to remove them however and quickly found that the actual player is suseptable to scratches, and once you remove the plastic covers, espectially if they get dirty, they may never seal all the way again. i threw mine away and dug them out of the trash a few days later and they just arent lasting because the hav become so dirty.

Operation: the menu is a typical heichal menu with a nice exception: now playing is the highest level. press the menu button to go up a level, and the enter button to select. The nice thing about 'now playing' being the highest level in the higherarchy makes it easily accessable by pressing the menu button untill you get there. Really operation is intuitive and self-explanatory, so i wont waste time detailing how to use it. it works well

blah blah blah, all that being out of the way now, we can get to the more useful things. if you want a review look to anythingbutipod.com for one good review, but keep in mind that any review you read may be out dated: meizu regularly updates the firmware in these players. when you purchase one, first thing to do is make sure you have the most recent firmware. in my humble opinion this is a really great mp3 player, but not perfect, as i will detail below. but hey, if you're even reading these forums chances are you arent afraid of a little work to make everyhting run smooth. and honestly, there isnt any work to it. but without some information a person may become most frustrated. 

compatibility: the m6 is 100% compatible with any computer that can use a usb port. mac, linux, windows, you name it, it works. When you plug in the player (turn the power on first if you want to transfer files, if you plug it in while powerd off, it will just charge the battery) it mounts just like any other flash drive or respectable mp3 player. the folders are self explanatory, with one for music, one for photos, videos, playlists, etc. just drag and drop the files you want into the proper directory (music in music, ect) and you are ready to go. its as easy as moving your collection with a flash drive.

using the m6 under ubuntu is a breeze, plug it in, copy the files, UNMOUNT, then you can unplug it. Here is something important for the fewest headaches: do not interrupt a file transfer once it has begun! and to be safest, i highly recommend dismounting the volume before unplugging from the computer. the reason for this is that if the transfer is interrupted, your files may become corrupt. this isnt a fault with the m6, its just the nature of the vFAT filesystem used on the flash memory. pressing Ctrl+c is a bad idea if you are using cp in the terminal to copy things over. and if you do interrupt a transfer, dont fel too badly, just know that many erratic behaviers in the m6 can be traced to that. Errors such as: "too many open files", or the volume becoming read only can be caused by corrupton in the vfat filesystem. the fix? format it and copy everything back. that simple.

now, the m6 is not the most flawless player out there. there are occasional glitches and hangs (most irksome to me, is that it will hang after browsing photos for a time) if it hangs, or doesnt want to shut off (turn it off by holding the power/play/pause button for 3 seconds) just hold down the menu button (the one with the m on it) for 8 seconds and it will shut off. power up and everything will work great! 

if you want to format it without using a tool from the computer, just hold down the >> button while you turn it on. to do a low level format (dunno the difference but there is one i guess) hold down the << button when you turn it on. 

encoding video for the m6 is best done with mencoder. scripts can be found on the meizu forums if you want to use one, i would recommend doing so because the encoding requirements of the m6 are somewhat mysterious and it can take a bit of trial and error to find the right settings. but with a properly encoded video, watching movies on the m6 would not be a bad experiance, teh screen is smaller than say a zune but still quite watchable, even subtitles are readable most of the time.

the firmware is the easiest thing to upgrade. you just download the firmware and copy the files onto the player, then unplug, turn it off, then when you turn it on again it will perform the system update. keep in mind it will format whever you upgrade the firmware, so backup your music. once it does that there is a second file in the archive from the meizu website you downloaded, and just put that file in. [Complete instructions and download link here]("http://en.meizu.com/userforum/forum_posts.asp?TID=363")
even though the screenshots are windows, its no different under linux, just moving files is all. if you get a wierd error message or something happens in the update proccess, just start over again.


hopefully that covers the basics, post any questions or comments and i will try to keep this up to date for a while.

---

### Post by zvi on 2008-03-06
I have been looking into these players a bit and have some questions.

1) do you know what the hardware is like? should this player be able to last well, and can it stand some abuse (if I happen to drop it on the floor or something like that)?

2) I keep on hearing about the firmware advances. I am okay with computers but definitely feel quite a bit behind compared to most of the ubuntu users, will I have any trouble installing the updates.

3) You talked of some freezing up, is this common, how often would i have to deal with something like this?


Although I have these questions still I would like to state that I found this review and guide quite helpful. Thank you.\\:D/

---

### Post by mooglinux on 2008-03-06
mmkay 1st, the hardware. its solid. i have dropped it a few times but never from very high or on a very hard surface. i suspect that it would take a rough tumble without much fuss, it certainly wont shatter like an ipod can. so i would agree that it is quite durable, just dont take off the plastic covering! with that on, nothing in the world will scratch it. i was smart enough to remove them however and quickly found that the actual player is suseptable to scratches, and once you remove the plastic covers, espectially if they get dirty, they may never seal all the way again. i threw mine away and dug them out of the trash a few days later and they just arent lasting because the hav become so dirty.

the firmware is the easiest thing to upgrade. you just download the firmware and copy the files onto the player, then unplug, turn it off, then when you turn it on again it will perform the system update. keep in mind it will format whever you upgrade the firmware, so backup your music. once it does that there is a second file in the archive from the meizu website you downloaded, and just put that file in. [instructions here]("http://en.meizu.com/userforum/forum_posts.asp?TID=363")
even though the screenshots are windows, its no different under linux, just moving files is all. if you get a wierd error message or something happens in the update proccess, just start over again.

as for the freezing, the only time i have had that happen is when viewing photos, and now that i figured out that fat32 doesnt do well when you disconnect it without unmounting, i have not encountered the problem since. then again i have not viewed a whole many photos either, but enough that before it would crash, but now it does not. happy times!

---

### Post by pjman on 2008-03-18
I have one of these also (M6 SL). I love the little thing. 

There is one limitation of the software that bugs me - If you have more than 128 songs for a given artists you will have trouble viewing the songs/albums using the "Music --> Artist" from the menu. "Music --> Albums" seems to work fine. Hopefully they will fix this with a future firmware upgrade.

[http://en.meizu.com/userforum/forum_posts.asp?TID=1929&PN=1](http://en.meizu.com/userforum/forum_posts.asp?TID=1929&PN=1)

---

