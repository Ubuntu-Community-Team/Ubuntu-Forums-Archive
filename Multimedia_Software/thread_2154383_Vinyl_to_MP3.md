---
title: "Vinyl to MP3"
date: 2013-06-14
forum: Multimedia Software
---

### Post by Barney-R on 2013-06-14
If this problem has already been dealt with elsewhere, I'd appreciate it if somebody could provide a link, though I'm not sure there **is** a solution.

I spent a little over £200 (UK) on a USB turntable, intending to transfer my old vinyl records to the computer.

I didn't want to pay a fortune for something that would be redundant when the job was done, but I didn't want anything **too** cheap either, like an old Dansette perhaps. I was **hoping** for a decent **quality** conversion.

Using Audacity, the input level from the turntable is too high, resulting in excessive clipping, and the relevant slider is greyed out, so I can't do anything about it.

Also, I'm getting turntable rumble and excessive surface noise - from records that are in near-perfect condition.

I've tried adjusting the tracking weight, and I've gone through the settings in Audacity, but nothing helps.

Is there a solution, or have I wasted my money?

Is Audacity the best software to use for something like this, or would something else be more suitable? Something with a scratch and rumble filter perhaps? Does such a thing exist?

I should point out that I'm a comparative newbie where this kind of thing is concerned, so if anyone knows of a solution, please keep it simple. I just want to convert about 4,000 tracks to MP3 without having to spend too much time on each one.

---

### Post by ajgreeny on 2013-06-14
So how does this turntable work?  What plugs into what?

You might have done better to buy a good normal turntable for less than £200, and then used a "phono to jack plug" cable and plugged it into the "line in" input of your sound card. You could then then use audacity to tecord the input.

I have never done that with a turntable, but I have certainly done it with an mp3 iplayer using a standard cable with a jack plug at each end.

I use audacity a lot, so may be able to help you if you give more info about what exactly you're doing.

---

### Post by jaweinre on 2013-06-14
> **ajgreeny said:**
> So how does this turntable work?  What plugs into what?

You might have done better to buy a good normal turntable for less than £200, and then used a **"phono to jack plug"** cable and plugged it into the "line in" input of your sound card. You could then then use audacity to tecord the input

I have never done that with a turntable, but I have certainly done it with an mp3 iplayer using a standard cable with a jack plug at each end.

I use audacity a lot, so may be able to help you if you give more info about what exactly you're doing.

No, PHONO is a different standard found on old turntables and tape recorders. It's impedance differs from LINE standard. If you connect a PHONO device into a LINE input, you'll get bad equalization and overall bad levels. That's why you need to get some form of amplification that includes a PHONO input.
Ofcourse you could try it anyways, it won't damage your stuff or anything. Just wanted to clear this out heh.

---

### Post by jaweinre on 2013-06-14
About the USB turntable issue, could you please be VERY specific about brand/model, cables you're using, laptop/desktop brand model, ubuntu version etc etc.
Things to consider:
Grounding. Is your turntable well grounded? Three prone wall outlet and all that. If you're using a laptop, try disconnecting it from it's charger, these usually produce electric noise, especially the cheap ones. Is your turntable connected to the same wall outlet as your PC/laptop?
Driver. Did the turntable come with drivers or anything that points to linux support.

---

### Post by coldraven on 2013-06-14
I hate to be a downer but any gadget that you see advertised in a newspaper supplement or "innovations" type brochure is quite likely to be rubbish.
Is your turntable belt driven?  If not then that would explain the rumble. You may see where this is going....
I bought an Akai tuner/amp and a Pioneer deck at a jumble sale for £4 about 15 years ago, it still blasts out sound really well.
I got a new belt for the deck from eBay when the old one perished.
As the old adage says, "If you want a job done well, do it yourself".

---

### Post by Barney-R on 2013-06-14
Thanks for the replies so far. I'll come back with more info as soon as possible, but something's come up and I won't be on-line over the weekend. Sorry. Got to go.

---

### Post by Barney-R on 2013-06-19
Sorry. That took longer than I anticipated. I hope this thread hasn't "died" in my absence.

The deck is a "Onestar" (perhaps I should have seen that as a warning), and it did come from one of those companies that distributes mini-catalogues in magazines. I'm not sure now whether it was "MySmartBuy" or "BrightLife UK".

I haven't removed the turntable itself (no circlip pliers, and I don't want to risk damage or injury by using a screwdriver), but I believe it's belt-driven.

It plugs directly into the mains (3-pin plug) and has two outputs, a twin phono which is too short to reach the computer anyway, and a USB.

It didn't come with any driver software, just an Audacity CD.

The computer itself is a high-end desktop model, with Asus motherboard, 8 core processor and enough RAM to ensure that it never needs to use the swap file.

My operating system is Ubuntu 12.04, 64-bit (single boot).

I don't know whether any of that helps, but I suspect I may have wasted my money on a deck that isn't fit for purpose.

---

### Post by Lars Noodén on 2013-06-19
Skipping ahead to when you've gotten the hardware solved, you'll probably only want to port from vinyl to digital once per disc.  In that case you should strongly consider making the first copy in a high resolution archival format.  FLAC is good for that as it is both lossless and allows embedding of considerable metadata.  Then from there you can make MP3s or whatever you happen to need in terms of lossy formats, resampling to a lower bits per channel and lower samples per second.

---

### Post by Barney-R on 2013-06-19
Thanks for that Lars. I don't know very much about audio formats other than .wav and .mp3, so I'll take your advice - assuming the quality problem can be solved.

If the deck really is rubbish, I'd appreciate any advice as to where I can get a decent one (I'm in the UK), and which make and model to go for now that they're no longer available through the shops.

Boot sales are out due to personal circumstances, and I don't get much chance to look in junk shops, so it will have to be new (or perhaps Ebay).

---

### Post by Barney-R on 2013-06-21
Hello??? Anyone here?

---

### Post by gordintoronto on 2013-06-21
You say the turntable has twin "phono" jacks? (I assume you mean RCA.) Get a cable which will take that to 3.5 mm stereo and plug it into line-in, or plug it into a small amp, and from there to line-in.

Alternatively, just bit-torrent download the tracks you legitimately own. I was capturing my favorite tracks, turntable to amp to line-in to Audacity. My son challenged me: "can you capture a track faster than I can bit-torrent it?" It wasn't close.

---

### Post by 23senick on 2013-06-22
Sorry I'm a bit late to the party, only just clocked the thread.  

I'd be suspicious of the turntable.  I rigged up my 30 year old turntable through the amp and into desktop PC.  One issue I had was sound cards, bulk standard ones may distort even if levels look OK.  But in the end all sounded great.

Hope I don't get booted off the forum for mentioning...I used a Windows-based programme called Wave Corrector (easy to find on google).  I can't recommend it highly enough - got rid of pops, scratches etc, even ones I thought beyond hope.  Haven't tried any Linux alternatives as it works so well.  It might deal with your rumble, but as I said at the start, I suspect that turntable.

---

### Post by Barney-R on 2013-06-22
**gordintoronto** - I'm not 100% sure of the legality of downloading tracks, but I've got about 4,000 to do, and a bandwidth limit of only 10GB a month. I haven't used Bit Torrent, but a lot of the older stuff on YouTube is of poor quality, and not everything is there.

I'll have to look into Bit Torrent, but my understanding so far (possibly wrong) is that it's a bit like the old version of Napster in that it's two way sharing, which would devour that monthly bandwidth allowance. I'll certainly investigate it though.

**23senic** - I don't use Windoze (or Wine), but what you said about Wave Corrector gives me hope of finding a solution if there's an equivalent that will work with Ubuntu.

You (and others) are probably right about it being the turntable though, certainly where the rumble is concerned. I'll keep trying for a bit longer, but it's looking as if I've wasted my money (and all those spare styli I bought with it :( ).

I'd appreciate it if anyone can recommend a decent turntable (available new if possible) that isn't ridiculously expensive, in view of the fact that it will be redundant when the job is done. Perhaps we'll be able to sort the present problem out, but I'd like to know what's available - **and good** - in case I do have to give up on the one I've got.

---

### Post by Barney-R on 2013-06-22
I don't really want to detract from the original purpose of this thread, which is lack of level control, turntable rumble and excessive surface hiss when attempting to use a USB turntable to copy vinyl records to the computer, but Bit Torrent has been mentioned, and I can't work out how to use it.

Seemingly as part of the original install, I have "Transmission BitTorrent Client" in my start menu, so I had a look at it, but it asks for a URL. How do I find a URL?

I've never used file sharing before, in case it's not obvious.

---

### Post by gordintoronto on 2013-06-22
I will try to provide the scoop on bit torrents...

If you own a vinyl record, it is completely legal for you to download an MP3 of that record. It's called "backup." Mind you, I am not a lawyer, so I can't provide legal advice. My guru on copyright is Brad Templeton: [http://www.templetons.com/brad/copymyths.html](http://www.templetons.com/brad/copymyths.html)

The starting point is Google. For example, I own Art Garfunkel's Breakaway album, and one of the songs is "I only have eyes for you." So I Google "I only have eyes for you garfunkel torrent" and get several results. The second one takes me to a site where there's a download link for a "torrent" file. (Torrents are quite small, typically a few dozen KB.) In my file manager, I right-click on the torrent, and select "open with Transmission...." Transmission opens up, but we're not quite done. I need to select the file I want and then click on "open." If you're lucky, the MP3 will be on your system in a few minutes.

The system is not perfect. You will come across sites which want you to install a "download manager" (for Windows) and most of them are pure malware.

You will also see the terms "seeders" and "leechers." A seeder is a person you is offering a file, a leecher is downloading. If you want a file and there are no seeders, you will never get it.

It's worthwhile to become familiar with bit torrent downloads, because on the day a new version of Ubuntu is released, by far the best way to get it is by bit torrent.

Clarification: the actual torrent I selected was for the entire Breakaway album -- and it downloaded in less time than it took to write this message.

Music files aren't very big. A typical MP3 is less than 10 MB. Even so, 4000 songs is a lot of data traffic.

---

### Post by coldraven on 2013-06-23
> If you own a vinyl record, it is completely legal for you to download an MP3 of that record. It's called "backup."
I agree that it is probably legal to download as a backup. The problem I see is that BitTorrent is also simultaneously uploading the file so you are actually distributing it as well. That's when the lawyers will descend on you like a ton of bricks.

---

### Post by Barney-R on 2013-06-23
Thank you both for the latest info. It seems I need to be careful due to the re-uploading issue, but I'll certainly investigate further and familiarise myself with the process.

---

### Post by SeijiSensei on 2013-06-23
I bought an [Audio-Techica USB turntable]("http://www.amazon.com/gp/product/B002GYTPAE/") from Amazon for about $100.  So far my experiences with it have been pretty mixed.

On my turntable, there is a physical switch that controls the output level.  You might see whether there is an equivalent adjustment on yours to avoid the over-modulation problem.

My problem is the loud tape hiss on my rather elderly albums.  This is especially noticeable on classical recordings with wide dynamic range.  I found I could do a decent job of filtering it out with Audacity by having it sample the first few seconds of a track before the music began.  Still the amount of effort involved in trying to make decent copies of the albums has put me off the enterprise for a while.

---

### Post by coldraven on 2013-06-23
Slightly off-topic but might have some resonance for USA readers:
During WWII my father was a stoker in the Royal Navy. The ship was torpedoed in heavy seas in the Atlantic and was holed above the water line. It managed to limp into North Carolina for repairs. During this time, presumably at a funfair booth, he recorded a vinyl 45 and sent it to my mother.
I have this record in my desk drawer but have never heard it. I keep meaning to make an MP3 but it would be strange to hear my father's voice from before I was born. Both of my parents are dead now.
Any thoughts?
Apologies to the OP but this just came to my mind. (three glasses of wine may have made me somewhat nostalgic)

---

### Post by alvinmoneypit on 2013-06-23
Here is a "[HowTo]("https://www.computerworld.com/s/article/9136270/Review_5_USB_turntables_convert_LPs_to_MP3s")" from computer world.  They have some of the better turntables that you might recognize. What you already tried might work in WINE.  Have you tried audacity in WINE for this?

---

### Post by alvinmoneypit on 2013-06-23
coldraven- museums and possibl;y veteran oraganizations would be interested in your dads' disc, undoubtedly many websites as well.  You should convert it to digital for them.

---

### Post by Barney-R on 2013-06-25
Thanks for the further replies, and apologies for yet another delay (called away again, sorry).

I managed to find a Torrent and was able to work out how to use Transmission, but no traffic. Turns out my ISP is one that blocks sharing, so that's the end of that. At least it seems I can (probably) download some of the tracks from YouTube without breaking any laws.

Sharing/downloading was a side issue anyway. The main thing is to get all that vinyl onto the computer. I'll check the Computer World article now.

Audacity's Noise Reduction works well in a lot of cases, but even sampling the "silence" at the beginning of a track doesn't seem to help with surface hiss and turntable rumble.

Obviously I'd like to use the equipment I bought specifically for the purpose, but so far it's looking as if I'll have to pay out again.

My own fault I suppose. Always go for brand names. The trouble is, without studying the market, and with turntables no longer available in the shops, it was a case of getting whatever I could.

---

### Post by VanillaMozilla on 2013-06-25
> **Barney-R said:**
> Using Audacity, the input level from the turntable is too high, and the relevant slider is greyed out....
Are you guys sure you're focusing on the problem?  The problem is that the input level is set wrong.  The user has a turntable that has phono outputs and a USB output.

So far you guys have discussed belt drive turntables, Bit Torrent, legal issues, and where to buy turntables, and just about anything except the question.  Furthermore, you've got poor Barney stringing along with you.  Did I miss something?

OK, Barney, I'll tell you what I know--which is, unfortunately, not quite enough.  The problem is that the gain is too high somewhere, so the problem is how and where to set it.

I don't know how these USB outputs from turntables work, or how you are getting music into Audacity.  I am told that a USB turntable just looks like a drive.  That means that the turntable should have done the work of amplifying the sound, equalizing it, and setting the gain.  That means the gain setting would be in the turntable.  It would have controls somewhere -- either on the chassis, or in software.  If the controls are software, they would require special software in the computer, and that almost certainly means Windows-only, or Windows plus Mac.

In other words, if this turntable is directly giving you sound files and Audacity shows you that the files are clipped, the gain setting is in the turntable.  Period.

Now, if you have an analog input into the computer, instead of a digital input, you are in luck.  Just go to the System Settings on your computer and look for sound.  Look around and push the buttons until you find the right input.

If you have a good sound card and want to go the analog route, you will need a pre-amp.  An RCA output requires a phono preamp, which includes the required phono equalizer.  That will give you a line output that you can connect to the sound card and record with an analog-to-digital recorder (your sound card plus Audacity is one way to do this).

If all else fails, read the directions.



One other point to consider, ***after*** you have solved the problem.  I belong to an organization that digitized several hundred vinyl recordings on a $100 USB turntable.  I got my hands on one of those records and digitized it myself on my old, modest AR turntable with Shure cartridge.  I have normal hearing for a 70-year-old, and I am not one of those audiophiles who imagines huge differences where there are none.  Nevertheless, I was absolutely shocked at the difference.  The $100 turntable was just awful.  The equipment doesn't have to be fancy, but quality does matter.  I think you need to get this working first, though, before you decide on quality.

---

### Post by VanillaMozilla on 2013-06-25
In another post you mentioned two other problems:  surface noise and rumble.  Surface noise is an inherent characteristic of vinyl recordings, especially if they are in poor condition, and that's really about all there is to say about it.  Once it's there, you can't take it out without taking something from the music.

There are a some ways of reducing it in some instances.  You've already tried filtering with Audacity, and that sometimes does an amazing job if rescue is your objective.  I've sometimes even had good luck with automatically removing clicks and pops, and if the automatic procedure fails, you can do it manually.  Good luck if you have thousands of LP's.  Probably better to present them as they are.  There are also needles available with an unconventional shape, so it rides in a relatively unused part of the groove.  For monaural records you can also wire the two channels in parallel at the cartridge, and that can cut noise somewhat in some cases.  You say both of these are beyond you?  Yeah, me too.

The rumble could be the turntable.  Or 60-Hz hum.  If all the wanted sound is above the rumble frequency, you can just filter it.  Otherwise you will remove some of the music.  Or you can get better equipment.  Read it and weap.

---

### Post by SeijiSensei on 2013-06-25
> **VanillaMozilla said:**
> That means the gain setting would be in the turntable.  It would have controls somewhere -- either on the chassis, or in software.

I pointed that out earlier in the context of my AudioTechnica turntable.  It has a switchable preamp.  My device only has on/off, though, not a variable gain control.

---

### Post by VanillaMozilla on 2013-06-25
SeijiSensei, good point.  You did say that yours has a gain switch.  It just doesn't make sense that turntable with a digitizer that always clips sound files has no gain control.  If Barney is using the USB port, the turntable must have a gain control *somewhere*.  If it doesn't, then it's unsuitable by design for its intended purpose, and should be returned for a refund.  If that's what he's doing, I do wonder if he read the directions, though.  ;)

I'm thinking, though, that he probably isn't using the USB port at all, but a line input to his computer.  In which case, he simply needs to look for the correct volume control in Ubuntu.  If we know what he was doing, then we could advise him, couldn't we?  ;)

---

### Post by d_in_Conduct on 2013-06-25
First, you need to find out what sound device your version of Linux is using to receive sound from the turntable.  I'm pretty sure every version of Linux has  a mixer or volume control or control panel for multimedia (or just audio).  Your mixer should show what devices are set up on your system and you should be able to adjust the volume from the turntable there if Audacity doesn't let you do it.  Make sure you have the latest version of Audacity, by the way.

Under Edit>Preferences>Quality set the default sample rate to 44100 Hz (standard sample rate for audio CDs) and default sample format to 32-bit float.  This will give you plenty of dynamic range to work with.  Record something from one of your vinyls.  (at this point you may want to export it as a .wav or FLAC so you won't have to record it again if you want to change something later.  The fewer times you play a vinyl record, the better)  Click and drag a few seconds to select some of it.  Hold down the Shift-key and click the play button. That section will run in a continuous loop.  Click on Effects > Equalization.  If the EQ graph isn't a flat line at 0 Db, click on the Flatten button.  Start dragging the sliders down at the left side until you can get rid of as much rumble as you can without losing anything you want to hear.  You can probably reduce anything below 40 Hz to zero.  Above that, reduce only as much as you need.  Above 1000 Hz start gradually lowering each slider a little more as you get higher in frequency.  You should be forming a nice little curve ending with the last slider at zero Db.  This may be all you need to do.

You can now play with the frequencies and see if there are some that might be better a little louder.  If you still have hiss, click on Okay to close the EQ.  Then click on Analyze > Plot Spectrum.  You might see a spike among the higher frequencies that might be your hiss.  But you might not, either.  You can try selecting the silence at the beginning of the recording then clicking Effects>Noise Removal.  The click on Get Noise Profile.  Click on Effects > Noise Removal again.  You can play with the sliders in Step 2 but they usually a pretty good where they are.  Click on Preview to hear how it is going to work and click on Okay to apply.  

Then you can export it.  Click somewhere in the gray area at the left end of the recording to select the whole thing, or click and drag the whole recording after the silent lead-in and click File>Export and select MP3 or whatever you want.

As long as your turntable spins at a steady RPM, the only thing that can be "awful" about it is the cartridge.

Hope you get this worked out.  It's going to be a lot of work, no matter what.

---

### Post by VanillaMozilla on 2013-06-25
d_in_Conduct, your mixer and recording advice is probably good.  I'm not so sure it's a good idea to save his files with a 1 kHz cutoff, however.  Or even a 10 kHz cutoff.  ;)

I'm thinking it might be also be a good idea to postpone any post-processing until he knows what he's doing, and then either to do nothing or to use more sophisticated noise-reduction methods.  ;)

---

### Post by d_in_Conduct on 2013-06-25
The main thing at the moment, of course, is for him to get good, undistorted recordings to work with.  I don't know what advice I gave that would result in 1 Khz or even 10 Khz cutoff.  I wouldn't knowingly do that, so I'm missing something.

You've already given him better advice than I did, anyway.  I just hope he has enough to get started.

---

### Post by VanillaMozilla on 2013-06-26
> **d_in_Conduct said:**
> Above 1000 Hz start gradually lowering each slider a little more as you get higher in frequency.
[QUOTE=d_in_Conduct]I don't know what advice I gave that would result in 1 Khz or even 10 Khz cutoff.[/QUOTE]
I meant rolloff, not cutoff.

---

### Post by Barney-R on 2013-06-26
Thank you all for taking so much time over this. Here's the URL for the deck I'm trying to use so you can see it for yourselves.

[http://www.mysmartbuy.com/p-404-Neostar-Vinyl2CD-USB-Turntable.html](http://www.mysmartbuy.com/p-404-Neostar-Vinyl2CD-USB-Turntable.html)

It's got a fixed lead with two phono plugs, and a removable USB lead, which is the one I'm trying to work with.

It can also record directly to CD - from vinyl or tape - but I haven't tried that yet because I'd rather not have to use (and waste) an intermediate device, especially as so many CDs would be needed.

It's covered in buttons (16 just on the front panel), and so is the remote control, but I can't see a gain control anywhere. It does have two buttons (+ and -) marked "recording level", which **should** be the same thing, but I don't think they have any effect on USB output. I'll try them again though.

One thing that makes everything that much **more** difficult is that it doesn't have any audio output of it's own (no speakers), so I have to start **recording** in Audacity to hear anything.

The computer was purpose-built about 3 years ago (£2,000), and I'm running Ubuntu 12.04 with Audacity downloaded via the software centre (center), which tells me it's version 2.0.0-1 ubuntu 0.1.

I'll have a play tomorrow, and I'll let you know what happens, but I'm expecting visitors, so may not get much time.

---

### Post by d_in_Conduct on 2013-06-26
In cutting a disk, the RIAA specifies  a gradual boost above 1 Khz and a gradual rolloff below with little or nothing below 20 Hz.  For playback, the opposite is applied.  He can also use the RIAA preset in Audacity's EQ to compensate.

Which is not to say that the RIAA curve is the correct one.  If the records are fairly recent, it should be the right one to use.  Older pressings should specify what curve was used somewhere on the jacket.  It's a starting point, though.

I did suggest that he save the file in a lossless format before applying any filters so he can go back to it.

---

### Post by VanillaMozilla on 2013-06-27
Ordinarily, the built-in preamp should take care of equalization.  It's possible but probably unlikely that it doesn't.  You don't want to apply it twice, as that will mess up the sound.  It's possible that this device comes with directions.

I don't understand how the sound is transferred over USB.  I've never used one of those devices, and never heard of this procedure.

---

### Post by Barney-R on 2013-06-27
I don't know what I did, but I've managed to reduce the input to a manageable level, presumably by fiddling with the settings in Audacity as the +/- "recording level" buttons **don't** appear to have any effect on the USB output levels.

This has made a very significant difference to the unwanted noise levels, and the turntable rumble seems to have disappeared completely, so perhaps **most** of the problems were caused by over-amplification.

I've got a lot of work to do, but it **is** now possible to clean the tracks to a "just acceptable" quality, so I think I'll settle for that for now.

The records (in most cases) are in excellent condition, having been cared for almost "religiously", and I'll still have them after copying, so it's not a disaster.

**Thank you all for your help**. I'm saving the originals as flac files as well as converting to mp3 after working on them, so as I learn more about Audacity, or if I find something better suited to the job, I'll have those to work with.

---

### Post by Barney-R on 2013-06-27
Oops! I've forgotten how to mark the thread as solved.

---

### Post by alvinmoneypit on 2013-07-04
"solved" routine in these forums is broken.  Go to your first post, click "edit post", then click "go advanced" then select "solved" at the top selector where you put in your distribution.

---

### Post by Barney-R on 2013-07-05
Thank you alvinmoneypit. I've done that now.

General update. I've managed to solve the input level problem by fiddling with my system sound settings, and I've been reading the Audacity Wiki that someone linked to. Turntable rumble seems to have disappeared, but I'm still getting too many clicks and pops from records that are in near perfect condition.

I don't need any more help (I hope!), but in case anyone's interested, I'm planning on installing one of the spare styli I bought in anticipation of the size of the job. It's not unheard of for a new stylus to be faulty. I'll let you know if it solves the problem. If not, I'll just have to be prepared to spend a lot of time "cleaning" the tracks.

Thanks again to everyone for your help.

---

### Post by VanillaMozilla on 2013-07-07
Er, Barney, phonograph records have clicks and pops.  They're caused by defects in the plastic or by foreign particles, not by the needle.  But very thorough cleaning sometimes helps immensely if the record is not actually scratched or worn.  I even get a lot of improvement by cleaning _new_ records.  For what it's worth, the Disk Doctor system works very well.

---

