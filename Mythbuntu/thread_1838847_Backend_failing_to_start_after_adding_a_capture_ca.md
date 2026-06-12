---
title: "Backend failing to start after adding a capture card?"
date: 2011-09-04
forum: Mythbuntu
---

### Post by SamuelCB on 2011-09-04
Hello everyone. Ok so today I was watching the gadget show and on it they setup a PVR computer using mythbuntu and so decided to give it a go myself meaning I am a complete noob!

Ok so I have so far managed to install everything correctly and all my hardware seems to be picked up correctly however I am now begging to get problems. 

When I click on Watch TV in the frontend it says that there is no capture card installed, so I run the backend setup utility to find the place where you add a new capture card. When I go onto capture cards it picks up my Hauppauge WinTV PVR-150 [ivtv] card all ok and allows me to add it. So after doing this I exit the backend setup and I am prompted to run mythfilldatabase, which I do. Once that is run I then start the front end again but now receive an error saying (could not connect to the master backend server. is it running? is the IP address set for it in mythtv-setup correct?) So.... I go back to backend setup and check the database settings which are as follows:

Local backend
IP address: 127.0.0.1
port: 6543
status port: 6544

master backend
ip address: 127.0.0.1
port: 6543

I believe these are all correct as I only have one computer running mythbuntu and it is acting as a frontend and the backend so should be pointing to itself? Correct?

I hope this is enough info to get some help as I really want this to work. Thanks.

---

### Post by klc5555 on 2011-09-04
Be sure you have added the PVR-150 as an "MPEG encoder" card (or MPEG2 encoder, however it happens to be precisely worded) and not as a "V4l analog" card, which will not work.  The backend may not start either unless you've gone ahead and set up a videosource, bound the videosource to the tv output of the card (probably /dev/video0) in Input Connections, and have either scanned for channels or at least set one up manually (since analog cards do not require the actual scanning process).

Beyond that, the place to look would be in mythtv's backend log (under /var/log/mythtv) to see what's going wrong when the backend is trying to start up.

---

### Post by SamuelCB on 2011-09-04
Hey thanks for the reply. Ok so I have gone into the backend setup and have chosen the capture card option and then have added my capture card with the following settings:

Card type: IVTV MPEG-2 encoder card
Video device: /dev/video0
Probed info: Hauppauge WinTV PVR-150 [ivtv]
Default input: Tuner 1
Tuning timeout (ms): 12000

Ok so hopefully that is all correct? Next I have gone to the video source option and added a new one but got a little confused. Now I live in Cornwall in the UK so have gone with the following settings.

Video Source Name: Main Source
Listings grabber: United kingdom/republic of ireland (radio times) (xmltv)
Perform EIT scan: ticked
channel frequency table: default

I then choose the configure option and choose the following options.

0 - UTF-8 (Unicode)
Default directory
0 - enable title processing
entered postcode
1 - freeview
then choose to add all

I hope this is all correct so far and before going to the input connection settings I will wait for the green light from you. Thanks.

---

### Post by klc5555 on 2011-09-05
Well, I can't speak to the grabber; I don't know what's used there. But the essential thing at first is just having a Video Source set up, even with "No grabber" for program scheduling information configured --the correct grabber can always be added retrospectively.

In Input Connections, bind the Video Source to the card input. 

Where does your signal come from? The PVR-150 is analog-only, so the stations are either delivered in analog format directly, or some cable-box or intermediary is converting digital stations to an analog output on a particular analog channel.

If the stations are being delivered in analog form directly, then scan for them on this card input in Input Connections. You may get a bunch of "UNKNOWN" stations, but that's of no immediate concern. 

If there is but one channel being used to receive feed from some sort of digital converter or cable box, then you can simply exit the Input Connections menu at this point, go to Channel Editor, an add this single channel (say "3", or "4") manually. Finish up in Channel Editor.

Make sure in Storage Directories that there is at least one directory set up for recording tv. By default this should have been set up at /var/lib/mythtv/recordings, but wherever is is it should not be in your home directory, and needs to be readable/writable by "mythtv" (Normally set up this way by default)  

Finish up, let mythfilldatabase run (which will likely produce mostly useless scheduling information at this point, pending further configuration) and then (simplest) restart the machine.

The backend should start with the boot process; when the frontend starts you should in theory be able to start "livetv" If the backend does not start, the next stop will need to be checking the backend log to see what went wrong with the backend starting up.

For a better and more complete discussion of most of this setup process, don't forget to check Mythtv's own install manual at [http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index)

---

### Post by SamuelCB on 2011-09-05
OK well I must admit that I have got a little confused by your last reply but think I know what your saying. When you say "Where is your signal coming from", I have a normal TV aerial which has a normal TV aerial cable connecting it directly into the TV in port on the back of the Tv card in my computer so nothing in between?

On the input connections screen I choose the top option which says:

[MPEG : /dev/video0] (tuner 1) -> (none)

Then I called this Main input, choose the video source as the one I added earlier and then selected scan for channels. However, on the next screen I am not sure what to choose for the channel frequency table as when I choose Europe west or east they both return the same result saying (Failed to find any new channels) so why might this be? It says that single strength is 99% and scan stays on 5% the entire time?

---

### Post by klc5555 on 2011-09-05
OK, first question. I don't know, since I'm splat in the middle of the US --is your terrestrial TV in Cornwall UK still analog, or did it cross over to digital? What little I've been able to decypher on the web for that part of the UK implies that terrestrial TV there may now be DVB-T. The PVR-150 is analog-only; you would need a different card for terrestrial digital, or you'd need some sort of digital transport adapter to tune the digital signal and convert to something the 150 can receive.

But if there is analog there to be received, analog scanning has itself been broken from time to time in various iterations of Mythtv since about version .023

You may have hit this bug.

But scanning is not strictly necessary for analog. Since you've chosen the your correct locale settings (including presumably europe-west in the frequency table) in the General setup page, you should be able simply to add any analog channels from 2 through 99 manually in the Channel Editor and mythtv should be able to tune their frequencies.

In the Channel Editor  with no scan having been completed you should find no channels listed in your single configured Video Source. You can use Add Channel from the menu to add a new channel to this Video Source. Indicating the channel's number (say, "5" or whatever) on p. 1 of the add channel menu; and the same channel number again on the line (around p. 3 of the add channel menu) that says "channel or frequency" should be enough to allow mythtv to tune to that channel. Other information, like name, xmltvid number, callsign, and whatever can be added later when the thing is known to work.

When a couple of the known stronger channels have been added in this fashion, you can save and exit the setup, and see whether a) the backend starts and b) whether livetv can be tuned to the stations you have manually added. If livetv works for these stations, the backend can again be stopped, additional analog channels added manually, and the other useful information for scheduling and recording can gradually be added in.

If, however, the backend fails to start, then you'll need to check the backend log for a cause.

---

### Post by SamuelCB on 2011-09-05
OK well that is most likely my biggest problem since we here in the UK no longer receive ANY analog signals and only digital. So I went on with the setup with no channels, and exited the backend setup. I then started the frontend and no longer received the backend error which is obviously great. I then clicked on watched TV and only received fuzz but the is of course because we have no analog signals.

I do have another means of watching TV however with a WinTV piece of hardware but it is only a USB one not a PCI so will that still work?

I am not sure exactly what type it is but the writing on it says:

WinTV digital terrestrial TV stick NOVA-TD Hauppauge
DVB-T receiver with diversity

---

### Post by SamuelCB on 2011-09-05
OK well after my last post I suddenly had the thought, "why ask if it will work, why don't I just try it lol" and so I did. I have plugged my USB TV stick into the back of my computer, the stick appeared in my capture cards list and so I selected it. Next I scanned for channels (with some difficulty as it kept saying it had no signal) but it did however find the main ones it seems. Anyway I then started the frontend and there was no errors, so moved onto the watch TV part and it worked! :D

Thanks for all your help and tomorrow I will attempted to record TV lol and maybe and another PC as just a frontend :S 

Wish me luck :D

---

### Post by klc5555 on 2011-09-06
Great!

You're on your way, it seems.

You should find that "manual recording" will work even with no grabbers configured, much the same as recording TV used to work in the old VCR-tape days.

When you begin to add additional channel information (callsign, name, etc.), rather than doing it from the Channel Editor, you may find it more convenient to tune to the station in livetv and then use the "e" key to bring up the on-screen editing menu.

Good luck! :)

---

### Post by SamuelCB on 2011-09-06
Hey, yea I think I have set the grabber up correctly as most of my channels now have names such as BBC1, BBC2 etc. and they also all mostly have icons which is great. As for the recording what key do I press to begin recording? and do I need to state where recordings are saved before I can record?

Thanks again for the help and for being patient with me being such a noob lol :)

---

### Post by klc5555 on 2011-09-06
Surprise! You're already recording. There's actually no such thing as "livetv" in Mythtv --what you've been watching is "very-recently-recorded tv" Everything mythtv records, including "livetv" goes into the same set of storage directories, which if left at Mythbuntu's default is "/var/lib/mythtv/recordings". Livetv which is not explicitly preserved as a recording (while watching or subsequently) expires and gets cleaned out by the system after a day.

If your grabber is pulling in actual program schedule information and assigning it to your channels, then there are very many ways to record.

From livetv, the "r" key saves what you're watching as a permanent recording. In livetv, "m" pulls down a menu, one of whose options is a program schedule, from which future recordings may be scheduled while you continue to watch whatever you're watching. 

Most other recording options will be found in the Schedule Recordings option under Manage Recordings from the main Mythtv frontend menu. You'll get the hang of it in short order.

Have fun!

---

### Post by SamuelCB on 2011-09-06
Ah ok that rather cool. And once again thanks for the info and I am sure I will be doing a lot of experimenting in the near future to record all sorts or programs. :)

---

