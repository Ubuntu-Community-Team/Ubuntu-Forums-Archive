---
title: "Installing and using VDR (DVR style recorder) for DVB HDTV on Ubuntu 12.04"
date: 2012-06-17
forum: Multimedia Software
---

### Post by fixitdude on 2012-06-17
What is VDR?

It works as a server (vdr-kbd) with multiple plugins, reading dvb mpeg from devices installed on the machine. And clients (vdr-sxfe) can be more than one kind (xine, mplayer, vlc ...) and running on different computers that output the stream (TV or radio channel). In this example, server and client run on the same machine.
The main plugin is vdr-xineplugin, but there are others . i.e a webserver (to control vdr remotely, program record timer, see epg...), weather, games (as modern tv-sets), and almost what you can imagine to see on a tv).

I am going to update this as I go along today....

First, install everything you need to make your DVR card or USB device work on your system. You should be running Ubuntu 12.04 because a lot of things have been updated in VDR and DVB in general, otherwise your mileage WILL vary.

Install and use "Kaffeine" to scan for channels and watch TV to make sure it works OK. This is the easiest way I found to get things checked out quickly.

If things go wrong, check "dmesg" and /var/logs/syslog for clues. Digital TV likes a strong signal, so try to use a good antenna, I made a simple dipole out of a 75 ohm connector and used two pieces of wire going horizontally. They also make a FM antenna that is a dipole out of the old 300 ohm antenna wire, you may have one from the old days. Why FM yo usay? Because you are dealing with 57 Mhz at the low end and up to 800 Mhz at the high end (US frequencies). It seems like the 800 Mhz part gets in OK because of the size of the silly thing so you don't have to be a perfectionist. Plus I live about 15 miles from the transmitters line of sight. This thing hangs in a window.

Install the package for VDR.

I want to use it from a command line or script REMOTELY to automatically record my favorite TV programs by KEYWORDS from the program guide sent over the air. That's the project.

If you want to just watch TV, Kaffeine is perfectly fine and it also has a record option from the program guide which makes it simple but NOT automatic or by keyword.

Plus the program guide is only a few hours ahead in the best case, so you can't record something 3 days in advance, or always get your favorite weekly show.

Once VDR is installed you have to enable it in it's config file /etc/default/vdr

# Change to 1 to enable vdr's init-script
ENABLED=1

Then you start it like this:

sudo /etc/init.d/vdr start

If you want to see it's commands by command line (on that machine locally or if you are SSH'ed in):

telnet 127.0.0.1 6419

Type HELP to get the list of commands. Simple ones are LSTC to see the list of channels (it's default stuff at first and probably wrong for your place). And LSTE to see the EPG data (Electronic Program Guide). CHAN changes the channel.

Remember, with DVB it takes time for it to get the program data from the CHANNEL YOU ARE CURRENTLY TUNED TO. It doesn't get data for all channels, you would have to scan them all to get a full list and a lot of channels don't have program data.

You will need a good list of channels in a properly formated channels.conf file for VDR to be able to tune properly, yea it's a pain but you have to do this.

Stop VDR if it's running:

sudo /etc/init.d/vdr stop

w_scan -fa -A1 -c US -o 7 > vdr-save-channels.conf

If everything went well you should have seen the list of channels on the screen as it found them and decoded the channel names (it does 2 passes so be patient, 2nd pass is where it gets the channel names). If not, I have seen Kaffeine trash the interface somehow when it quits. Sometimes Kaffeine won't start again and get picture, very strange and I have to unplug the USB DVB device and wait a 30 count then plug it back in and then I get a scan OK.

You can look at the dr-save-channels.conf and see how it went. We will now copy it to where VDR wants it:

sudo cp vdr-save-channels.conf /var/lib/vdr/channels.conf

Now let's get things going!!

sudo /etc/init.d/vdr start

Now telnet in as above and check the channel list ( LSTC ) and change to a channel:

CHAN KXXX

Then see if there is program guide data, you should know that you have gotten program data from this channel before with Kaffeine, and this may take a little time to come in from the station.

LSTE

You can force a scan of all channels if the device is not busy recording:

SCAN




Links I found and referenced here:
VDR - how to start
[http://ubuntuforums.org/showthread.php?t=836171](http://ubuntuforums.org/showthread.php?t=836171)

VDR and Ubuntu
[http://ubuntuforums.org/showthread.php?t=993837](http://ubuntuforums.org/showthread.php?t=993837)

Simple VDR Protocol (SVDRP) allows simple commands to be sent to VDR over a plain TCP connection on port 6419
GOOD LIST OF COMMAND AND WHAT THEY DO!
[http://www.linuxtv.org/vdrwiki/index.php/SVDRP](http://www.linuxtv.org/vdrwiki/index.php/SVDRP)

Misc reference:

Standard channel info for other programs is located here after you install dvb-apps ( sudo apt-get install dvb-apps ):
/usr/share/dvb/

---

