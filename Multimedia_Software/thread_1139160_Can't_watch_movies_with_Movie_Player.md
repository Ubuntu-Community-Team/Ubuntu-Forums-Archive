---
title: "Can't watch movies with Movie Player"
date: 2009-04-26
forum: Multimedia Software
---

### Post by hapkidoman on 2009-04-26
Hey everyone!  I can't seem to be able to watch movies in movie player.  I've installed Ubuntu 9.04 about three weeks ago.  Since then, I've installed all of the medibuntu repositories but still can't seem to watch a dvd.  I can watch the dvd using VLC media player but not with movie player.  Also, when i use the command line:  sudo apt-get install libdvdread3, I get the error that it can't find the package libdvdread3.  How do I install that?

Also, I can't seem to burn an .iso image of my dvd using Brasero.  Any tips on how to get this stuff working right?  Other than that, Jaunty is fantastic, I'm so surprised at how smoothly everything runs!!!

**I just got mplayer (xine) to work........however, I can't install libdvdread4.  When I run the command line sudo apt-get install libdvdread4 it says that Super-user privileges are required.  Please run this with 'sudo'...what gives?

---

### Post by hapkidoman on 2009-04-26
Here is the error message I get when I try to burn an .iso image using brasero:

Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_current_track
BraseroDvdcss called brasero_job_set_output_size_for_current_track
BraseroDvdcss stopping
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_session_output_size
BraseroDvdcss output set (IMAGE) image = /home/chip/brasero.iso toc = none
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_set_use_average_rate
BraseroDvdcss called brasero_job_set_current_action
BraseroDvdcss called brasero_job_get_current_track
BraseroDvdcss called brasero_job_set_current_action
BraseroDvdcss called brasero_job_get_fd_out
BraseroDvdcss called brasero_job_get_image_output
BraseroDvdcss called brasero_job_error
BraseroDvdcss finished with an error
BraseroDvdcss asked to stop because of an error
	error		= 1
	message	= "Error while reading video DVD (no error)"
BraseroDvdcss stopping
Session error : Error while reading video DVD (no error) (brasero_burn_record burn.c:2599)

---

### Post by Bakon Jarser on 2009-04-26
Try running

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by hapkidoman on 2009-04-26
I already have those installed and it still does not work properly.

---

### Post by Bakon Jarser on 2009-04-26
Do you have libdvdcss2 installed?

---

### Post by soldar79 on 2009-04-26
You'll have to check this out, I guess

[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by hapkidoman on 2009-04-26
I've installed medibuntu, that's the part I don't understand....it should be working.  I had everything working flawlessly in 8.10, so maybe its a bug in Jaunty?

---

### Post by mdpalow on 2009-04-29
I just updated QuickStart to install DVD codecs for 9.04, so give it a try and you should be good to go after. Link is in my signature below.

Good luck,

mdpalow

---

### Post by Orographic on 2009-05-20
I have just installed Ubuntu 9.04 (fresh install) and can't install Quickstart properly from the link in your post. I had it running perfectly in 8.10.

When I install it via your instructions, it then tells me that it cannot install codecs for my version of Ubuntu (9.04). Then it tells me there is an update so I select update from the menu and then it says 'finished!'

Then I reboot and it still keeps telling me I need to install an update.

It also keeps telling me that my version of Ubuntu can't have Quickstart install the codecs.

What is happening?

---

### Post by Orographic on 2009-05-28
Any help on this? I went to the quickstart forums but no help there either.

---

### Post by xzero1 on 2009-05-28
> When I run the command line sudo apt-get install libdvdread4 it says that Super-user privileges are required. Please run this with 'sudo'...what gives?That is the way it is supposed to work. "Sudo" is required for any installation command in Ubuntu. This is for protection/security reasons. Simply use sudo and give it your password.

Please see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

