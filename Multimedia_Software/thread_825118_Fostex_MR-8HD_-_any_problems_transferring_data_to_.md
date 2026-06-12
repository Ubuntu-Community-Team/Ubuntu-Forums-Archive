---
title: "Fostex MR-8HD - any problems transferring data to Ubuntu PC?"
date: 2008-06-10
forum: Multimedia Software
---

### Post by cpetercarter on 2008-06-10
I make speech podcasts for people who are learning English ([http://www.listen-to-english.com](http://www.listen-to-english.com)). At present I record on an Edirol R-09, but I am thinking that I should upgrade to something which might give better recording quality, such as the Fostex MR-8HD. The Fostex records onto its own hard disc, and has a USB connection for transfers to a PC. My experience has been that Ubuntu (I have Hardy Heron) is pretty good at recognising USB connected devices. But before I commit to a purchase, I would be most interested in hearing whether any other Forum users have experience (good or bad) of using the Fostex machine with Ubuntu.

---

### Post by cpetercarter on 2008-06-12
Bump

---

### Post by jinnan_tonnix on 2012-01-30
YES!!!!

I know the thread is four years old, but I couldn't find any other mention of the Fostex.

However, the good news is that the Windows software will work with only a minor tweak to Wine.

Here's how:

First, you'll need to get the Windows version of Fostex's Wave Manager software.
[http://www.fostexinternational.com/docs/tech_support/wav_manager.shtml](http://www.fostexinternational.com/docs/tech_support/wav_manager.shtml)

If over time, the link becomes invalid, search for Fostex Wave Manager.

If you haven't already installed WINE, you'll need to do this now.


For some reason, the Wave Manager program will only look at drive D and this must be configured as a floppy drive.

Using a USB cable, either:

[LIST]
[*]Connect the Fostex and switch it to its USB mode, from the menu.
[*]Or, it's easier if you have a card reader; connect the card reader with the memory card in place.
[/LIST]

[LIST=1]
[*]Configure Wine (in Unity type 'wine' then choose Configure Wine)
[*]Under the Drives tab, remove any drive which may already configured as 'D'.
[*]Click the 'Add' button, then choose drive 'D'
[*]Click the 'Browse' button, and choose the folder into which the memory card is mounted (it will be something like /media/FOSTEX)
[*]Click 'Show Advanced' and choose 'Floppy disk' from the drop-down list under the 'Type' section. *** THIS IS CRUCIAL ***
[*]Click OK
[/LIST]

Now launch the Fostex software by right-clicking the WAVManager.exe file and choosing to launch with Wine.

With luck, you'll be able to see the song folders and their wave files.

Enjoy!

---

