---
title: "[help] required to fix a few problems! (Channels, Linux)"
date: 2008-10-20
forum: Mythbuntu
---

### Post by WoodsieLord on 2008-10-20
WARNINGS: I'm an Linux newbie. I'm a TV newbie (half true)

Hello everyone, I'm new to the forums. I came here in hope for some help or tips to get into the right directions. I should apologize in advance cause my english skills are not very good. Ok here I go!:

After LOT of trouble, after a full week testing various MythTV distros I got Mythbuntu working quite good. I'm new to this HTPC world so I mean I can watch and tune channels in this setup. I still have no sound (not even the little stereo bridge to the sound card) but this doesn't bother me yet. I have two mayor problems that I don't know how to handle right: Channels and Linux. I'm almost sure my problems are software related but just in case I'm appending my setup specifications at bottom.

I'll start telling my channels problem. But first I need to explain my situation: I live in Argentina. No XMLTV technology available here. In fact, the word Digital is quite hard to find!. In other words, there is no way to magically get channel information, shows information, shedules, icons... nothing. Also note that my setup lacks network access. 

So, I scanned channels from the backend setup. The result was painful but beautiful at the same time. If I select "Argentina" for channels frequencies I get none picked up. I had to switch to "Try-all" and I got it sorted out somehow! The beautiful part: I got channels! I can watch them just fine. The painful part: My TV-Cable provider delivers ~70 channels and the Scan retourned ~250 results. Of course, only ~70 channels work, but there is more. The channel numbers are spread from 11 to 517.
- For every good channel I have, there are two neighbour noisy-channels.

A few hours ago, I just finished configuring channels from the Backend config. This is what I did:
- I grabbed my paper TV guide.
- I made a list from my working channels and their "new" numbers.
- I renamed the working channels to ***### - name*** and deleted the channel numbers for each non working noisy-channels. This step took me two days. I selected hide channels without numbers.

The result is half good: when Watching TV, I don't have the non working channels anymore, but ALL the channels still show as "unknown". So, I have no names nor numbers... If I wish to record Modern Marvels, normal people grab their TV guide (if they don't remember the Discovery channel number) and setup their VCRs to record that channel number. I just don't want to check a TXT file every time! (I saved my channel list in a TXT file to translate my ~70 channels to the ~500 format). I tried switching to "number name" and "name" only from the General TV setup options. I just don't know what to do.

The other issue, "Linux" is just too obtuse to find out just now what the problem may be. I'm afraid my knowledge is quite limited in the linux field. The symthom is quite simple to describe though: The system behaves different every time I start it. At first it went just fine, after 2 or 3 standard soft-reboots it stopped loading any GUI at all leaving me at the login echo. Fine, a simple google seach lead me to try "startx" while logged in. This brings a new different gui from the first I've seen but the menu has the same shortcuts so I don't care. The problem is that sometimes the "startx" command does not work. I just insist a few times and it starts working. I know I should blame myself for this, I mean, this randomness is not normal I suppouse. I hope once I get this setup sorted out it will behave more normally...

Well, this is it. I hope someone can shot some hints for me. Thanks a lot in advance.

My hardware:
MSI K7D MasterL
2x AthlonMP 2100+
1GB Reg. DDR ECC.
30GB HDD IDE.
Tuner: Pinnacle PCTV (bt878) correctly detected.
input: keyboard and mice for now :P
(if more info is required, just ask!)

---

