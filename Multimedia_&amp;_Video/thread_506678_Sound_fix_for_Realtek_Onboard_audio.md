---
title: "Sound fix for Realtek Onboard audio"
date: 2007-07-22
forum: Multimedia &amp; Video
---

### Post by etiennepb on 2007-07-22
I've been having sound issues with my onboard Realtek audio and have finally got it going. Pretty simple actually(after hour of searching).

First off I installed libcurses: 
> sudo apt-get install libncurses5-dev

Reboot.

Then I downloaded the latest drives from Realtek [[COLOR="Grey"]here[/COLOR]]("ftp://209.216.61.149/pc/audio/realtek-linux-audiopack-3.5-6b.tar.bz2").
Extract the file, then
> cd /directory/of/extracted/files/
sudo ./install

I hope this isn't a redundant post.
Peace,
Etienne

---

### Post by ntlam on 2007-07-22
is your computer a desktop or a laptop? I got a problem with my toshiba satellite u305. the sound doesn't work even i've been trying a lot of suggestion in this forum. anyone has any idea? my sound card is realtek too.
thanks a lot

---

### Post by fredj on 2007-07-22
You need the exact model number for your card but its always worth looking for a Linux driver on the
Realtek site.

---

### Post by ntlam on 2007-07-23
I just got my sound. 
toshiba u305-s5077
sound: realtek ALC268

Here is what I did. Hope it helps someone else with the same problems:

1. install required tools using:
sudo apt-get install build-essential ncurses-dev gettext

2. install kernel headers using:
sudo apt-get install linux-headers-`uname -r`

3. sudo mkdir -p alsa-src

4.download alsa* from: [http://www.alsa-project.org/](http://www.alsa-project.org/)
what you need are 3 files: driver, library and utilities. save these files to the directory: ~alsa-src

5. extract the files: (at the moment the latest version is 1.0.14)
sudo tar xjf alsa-driver-1.0.14rc4.tar.bz2
sudo tar xjf alsa-lib-1.0.14rc4.tar.bz2
sudo tar xjf alsa-utils-1.0.14rc4.tar.bz2

6. Compile and install alsa-driver:
cd alsa-driver-1.0.14
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install

7.Compile and install alsa-lib:
cd ../alsa-lib-1.0.14a
sudo ./configure
sudo make
sudo make install

8.Compile and install alsa-utils:
cd ../alsa-utils-1.0.14
sudo ./configure
sudo make
sudo make install

9.reboot

at this point I did not get sound yet. Then I did steps:

10. downloaded from: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104)   
the file realtek10.tar.gz. Extract this file. then  copy the 2 files hda_proc.c and patch_realtek.c in the folder "realtek10.tar.gz_FILES" to:
/alsa-src/alsa-driver-1.0.14/pci/hda

11. edit the file patch_realtek.c by using:
sudo gedit patch_realtek.c

go to "search"-->"find" then type "static int patch_alc268" ---> "enter". Then you see the following: 


static int patch_alc268(struct hda_codec *codec)
{
	struct alc_spec *spec;
	int board_config;
	int err;

	spec = kcalloc(1, sizeof(*spec), GFP_KERNEL);
	if (spec == NULL)
		return -ENOMEM;

	codec->spec = spec;

(remove code from here)

	board_config = snd_hda_check_board_config(codec, ALC268_MODEL_LAST,
						  alc268_models,
						  alc268_cfg_tbl);

	if (board_config < 0 || board_config >= ALC268_MODEL_LAST) {
		printk(KERN_INFO "hda_codec: Unknown model for ALC268, "
		       "trying auto-probe from BIOS...\n");
		board_config = ALC268_AUTO;
	}

	if (board_config == ALC268_AUTO) {
		/* automatic parse from the BIOS config */
		err = alc268_parse_auto_config(codec);
		if (err < 0) {
			alc_free(codec);
			return err;
		} else if (!err) {
			printk(KERN_INFO
			       "hda_codec: Cannot set up configuration "
			       "from BIOS.  Using base mode...\n");
			board_config = ALC268_3ST;
		}
	}
(to here)

then you have to remove the above code and add a code right there:
    board_config = ALC268_TOSHIBA;

--->save the file and exit

11.(cont.) go back to /alsa-src/alsa-driver-1.0.14/: cd ../..

12. do the following:
./configure
make
sudo make install

13. cd /etc/modprobe.d/

14. sudo gedit alsa-base

then add the the following code to the bottom:
options snd-hda-intel index=0 model=toshiba

15. reboot

16. do the command:
alsamixer
then maximize the volume

hope you get the sound then.

---

### Post by MCMcButtah on 2007-08-07
Thanks so much ntlam, your instructions worked for me where nothing else did. I tried a bunch of similiar instructions without success. I was using the newer realtek12.tar.gz. rather than realtek10.tar.gz. before so maybe that was it. Also /etc/modprobe.d/alsa-base did not exist until after a reboot, but when I rebooted I had sound so I didn't bother to make the edit. Thanks again!

BTW: I also have the U305, have you been able to get everything else to work...webcam and such?
I'm gonna try the fingerprint reader next.

---

### Post by ntlam on 2007-08-07
I am still looking for webcam and microphone solutions. If you got success let me know. Thanks

---

### Post by dehuszar on 2007-08-11
The webcam should work on any v4l2 compatible app.  Using Ekiga, I can see myself with the WebCam.  Using v4l1 apps, no dice.  As for the microphone, using the above instructions, I can only get OSS to work, so I'm having issues getting the sound in apps like Ekiga to work as it wants ALSA.  

Running the audio tests from the Preferences->Sound app gives me this error:

> audiotestsrc wave=sine freq=512 ! 
audioconvert ! audioresample ! gconfaudiosink: 
Could not open resource for writing

I'm experiencing this witha Satellite U305-S5097, same audio chipset, and I assume the same Chicony Webcam.

---

### Post by ntlam on 2007-08-16
I just got my ubuntu deleted by accident. I had to install a fresh one. But I haven't got the wireless yet even though I tried a lot of suggestions.
I guess you have the same wireless chip with mine. Do you remember how you did to get the wireless work?
my info about the wireless is: Atheros AR5007EG 
Thank you

---

### Post by dehuszar on 2007-08-16
I don't remember the exact link I used, but you should be able to get a link from just doing a google search for the model# and "winxp driver".  With the appropriate driver, the standard procedure for ndiswrapper should do the job.

Worked fine for me.

---

### Post by jediackbar on 2007-08-16
I just installed Ubuntu on my laptop, a Toshiba Satellite U305-S5097.  The sound fix by "ntlam" was amazing.  I worked great.  Thanks!  

Does anyone have any info about getting the wireless to work?  I am really interested in using/learning linux because vista leaves much to be desired.  I'm an advanced XP user, but a complete novice with linux,

---

### Post by ntlam on 2007-08-16
I just got my wireless back.
[http://ubuntuforums.org/showthread.php?p=3202754#post3202754](http://ubuntuforums.org/showthread.php?p=3202754#post3202754)

---

### Post by jediackbar on 2007-08-17
Whenever I plug headphones into the jack on the side, I hear sound through both the speakers and headphones.  Any ideas on how to 'turn off' the speakers when headphones are plugged in?

---

### Post by ntlam on 2007-08-17
double click on the volume icon and you can choose to turn one of them off

---

### Post by ntlam on 2007-08-19
> **dehuszar said:**
> The webcam should work on any v4l2 compatible app.  Using Ekiga, I can see myself with the WebCam.  Using v4l1 apps, no dice.  As for the microphone, using the above instructions, I can only get OSS to work, so I'm having issues getting the sound in apps like Ekiga to work as it wants ALSA.  

Running the audio tests from the Preferences->Sound app gives me this error:



I'm experiencing this witha Satellite U305-S5097, same audio chipset, and I assume the same Chicony Webcam.

How did you install the driver for webcam?
I haven't got success yet.

---

### Post by dehuszar on 2007-08-21
If you search for 'webcam' in Synaptic, you will see a couple of driver packages, specifically the spca5xx-source package.  Installing that should give you V4L2 compliant drivers and should work in apps like Ekiga.  Apps which only support V4L, such as Wengophone, I haven't found a solution for.

---

### Post by ntlam on 2007-08-21
thanks
I will try that

---

### Post by ntlam on 2007-08-21
Now I can see myself with Ekiga. I tried with kopete but there was just green image.

---

