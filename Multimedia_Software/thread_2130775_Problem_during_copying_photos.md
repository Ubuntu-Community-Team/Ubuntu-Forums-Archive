---
title: "Problem during copying photos"
date: 2013-03-30
forum: Multimedia Software
---

### Post by peter2013 on 2013-03-30
Hello,

I'm encountering some problems when I'm copying my photos from my Canon EOS 1100D digital camera. When I drag the map (called 100CANON) of the internal memory of my camera to a location of my computer, the copying is stopping after a while. In order to close the window of copying, I have to turn of my camera. (Switching on is necessary in order to copying)

It's remarkable that the photos which are copied before this moment can be opened. It is also no problem to copy all the photos to the iMac of my girlfriend.

Can somebody offer me a solution for this? I'm using Ubuntu 12.04 on a HP Pavilion.
Thanks in advance!

Peter

---

### Post by sudodus on 2013-03-30
Welcome to the Ubuntu Forums :-)

Does the copying stop before or after all files are copied?

Are you running Ubuntu with Unity and using the default file browser (Nautilus)?

What happens if you use ***Shotwell*** to import your photos (instead of the file browser)?

---

### Post by peter2013 on 2013-03-30
Hi Sudodus. Thanks for the welcoming ;)

The copying stops _during_ the action. You can see all the tiles in the target map, but you see only the miniatures of the photos loaded before the 'crash'.

Yes, I'm using the default file browser, and I use Ubuntu with Unity.

When I use Shotwell I get also all the tiles, but with a prohibitory sign.

---

### Post by sudodus on 2013-03-30
Will Shotwell import no files or some files? Please describe the prohibitory sign!

How did you mount the camera? What happens if you unmount the camera (without physically disconnecting it) and then start Shotwell? Will it find the camera? Maybe it works better 'when connected as a camera' instead of 'when mounted as a file system'.

Do you have a card reader, that can read the flash card?

---

### Post by peter2013 on 2013-03-31
Shotwell import no files: the tiles of _all_ the files are visible, but _not one_ shows the miniature (= little photo). This is in opposite with the default file browser, where _some_ miniatures are loaded and visible.

The prohibitory sign in Shotwell do you find via [this link]("http://1.bp.blogspot.com/_IYhM1Uq_ADg/TU9BDPzze7I/AAAAAAAAAFE/oaUl0g2UDWo/s1600/Three%2BPigs%2B-%2BProhibitory%2BSymbol.gif").

I physically mounted the camera with the cable, and Ubuntu asked which action I would do (open in Shotwell, open with file brouwser, ...). I have set it to open it always in the default file browser (and selected 'Never asks this again'). So, when I now connect my camera, the file browser opens automatically.

When I unmount the camera and start Shotwell, he finds the camera and shows the files with prohibitory sign.

I think the device is connected as camera, and not as a file system. In the file browser I see below 'devices' a icon of a camera named as 'Canon Digital Camera'. When I bring my mouse to the name (without clicking), the label gphoto2://[usb:001,007]/ appears.
(If you think the device is connected as a file system, can you tell me how I can connect it as a camera?)

No, I don't have a card reader. Maybe I have to buy it ;)

---

### Post by sudodus on 2013-03-31
That prohibitory sign shows that the file is not available no read access. You are right, it is connected as a camera (not mounted as a regular partition), when it shows the label gphoto2://[usb:001,007]/. So if I understand correctly, you tried 'the normal mounting and reading with the file browser' and it did not work. And now, Shotwell doesn't work either. It is possible that the flash card is damaged, either physically or logically (that the file system is corrupted). Or that the camera or connection (cable) is damaged. Is the camera swithed ON? Is there enough battery power?

The first thing to do is to ***be sure you have saved all the pictures*** via your girl-friend's Mac.

There is probably a Windows file system (FAT32) on the flash card, and it is best to repair it using a Windows tool, so from Windows (maybe in another computer), if you want to try to run ```
chkdsk /f
``` or the GUI front end tool to check/repair the file system.

But it is easier to simply format the file system again, either with the camera itself, if it can do it, or with linux.

If you want to format it with linux, you need to mount it with the file browser again, and then use
```
gksudo gparted
```
Select the flash card from the small dropdown menu at the top right corner and format the existing partition to FAT32. Click the tick icon at the top of the window to perform the selected action.

If this does not work, you can try with a USB flash card reader. If still no go, your card is probably physically damaged (bricked), but we are not there yet, you have a fair chance to get the card working again.

---

### Post by peter2013 on 2013-04-01
You understand it correctly, Sudodus.

Although I have done several formats on the camera, I did it again in the internal card reader of the iMac of my girlfriend. Unfortunately same result.

If you say that maybe the card is damaged, why does it work on the iMac?

Concerning the battery power and the ON switch: I'm sure you can eliminate this options.

---

### Post by sudodus on 2013-04-01
The card might be dying. Sometimes a flash memory becomes read-only (cannot be written, formated etc) and finally it refuses reading too. But often there is file corruption, that can be repaired. The card can be read but not written in the Mac. Maybe the card reader has better signal to noice ratio or a more patient driver (rereading if bad signal) or something like that.

Cards are rather cheap today, so get a fresh one when you have saved the photos. I would not take the risk that the next set of pictures will get lost.

---

### Post by piperbarb on 2013-04-02
If  you have another SD card, format it in the camera if possible,  take some photos using that card, and try to transfer the files.  If you still get the same result, try a different USB cable or a different USB port on your computer.  It could be that.  I have never had problems uploading files from my camera to my Ubuntu laptop (12.04 64bit).  I do have a card reader built in to the laptop.  I just copy the files from the SD card to the directory where I put my RAW files prior to processing.

---

