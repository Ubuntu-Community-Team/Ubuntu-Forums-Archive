---
title: "Mythexport sssssslllllllooooooowwwww"
date: 2010-08-31
forum: Mythbuntu
---

### Post by sydneysuder on 2010-08-31
Hi,
Until recently I had no need to use mythexport. I got an Ipad last week and decided to go ahead and try this feature.
I have managed to get it working but it is extremely slow. It takes about 6 times longer than the recording it is converting.

I have installed the airvideo server (via wine not the native linux one) and converting the same file it takes 1/2 the time
of the recording.

For example:
Program		: Monster Moves AUG 28
Format		:HD 720P
Size in Myth	:1 hour  5 minutes (4.9GB)
time to convert in myth export: 7 hours (and then I cancelled)
size mythexport:	657 MB when cancelled
time airvideo	: 36 Minutes
size export airvidieo: 537MB


The machine is a VM running on Citrix Xen Server 5.5 and has been configured with 4 CPUS, 1 GB of ram and 500 GB of HDD space.
The Underlying CPU is an Intel Core 2 Quad Q9400 @ 2.66GHz.

I understand that both mythexport and airvideo use ffmpeg (as far as it is a requirement for both) so I am not sure what the difference could be.
However I noticed the following:

1. Myth took about 3 hours to actually start writing the converted file. During that time the two companion files xxx264.xxx. and ffmXXX.XX were being
populated.
2. When Mythexport was doing the conversion ffmpeg was running at 100% on only one core. It would jump around cores every 10 minutes or so
but it never used two cores at the same time. As a result the total CPU usage was always < 25%.
3. When Airvideo was doing the conversion all 4 cores ran at  ~80%  for the whole 36 minutes.



INFO ON THE MYTH SETUP

Version :  Mythbuntu 9.10 which was upgraded to 10.4LT by upgrading Ubuntu, enabling the myth repos and enabling 0.23.1 as the target version
MythExport:  Hacked the script file (can't remember the name) to use libfaac instead of lamemp3 (so that I could sync the files with Itunes)
			The conversion job is configured as follows
						- Resolution : 704*576
						-Aspect: 16:9
						-Audio rate: 192kb
						-Video rate: 1800kb
						-Codec: h264
						- Remove commercials= yes
						-Audio channels: 2
			The job is not setup to run automatically. I run it by showing the recording details in mythweb and then clicking on the third Job "Convert to Ipod" that I setup

Why those conversion settings? I did a test run with the same settings except the video rate was at 600Kb. It was a standard def file and only 29 minutes long. The output looked good on an iphone but too pixelated on the ipad. I converted the same file using handbrake (on a different computer so I wasn't comparing conversion times) with the "universal" preset which looked great on the ipad. I checked the file's details and the only difference with the mythexport one was the video rate so I changed that in mythexport.


I rather use mythexport for the file/job management capabilities but at those speeds It is useless for converting files on a regular basis.

Any suggestions will be greately appreciated.

---

