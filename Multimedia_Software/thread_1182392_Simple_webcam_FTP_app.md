---
title: "Simple webcam FTP app?"
date: 2009-06-08
forum: Multimedia Software
---

### Post by Razmear on 2009-06-08
I posted this question about a month ago with no replies, so I'll try again. 

I have a simple goal, to use my webcam to take a pic every 30 seconds and upload that pic via FTP to my webhost with a unique name for each image.
 
webcamd almost works, but there seems to be no way to change the file name (at least at my skill level) so it just keeps overwriting the last pic. 
I've tried several other apps by searching thru Synaptic with no joy. 

There are probably a hundred apps out there for windows that do this task, I can't believe that there isn't one out there in the Linux world that can do this simple task. 

Any help would be greatly appreciated. This is being setup due to some home security concerns, so I'd like to get this resolved and up and running as soon as possible. 

eb

---

### Post by Razmear on 2009-06-09
Anyone? 
Anyone? 
Beuler? 
Anyone?

---

### Post by pastalavista on 2009-06-09
I believe PiTiVi may have plugins that do what you want.

---

### Post by Dragonbite on 2009-06-09
There should be a means via scripting to do that. 

Alas, I don't know enough about scripting to help, but a cron job that takes a picture and ftp's it doesn't sound too far fetched.

What about all those people who say they want to program? Here's one for ya to do!

---

### Post by Razmear on 2009-06-09
I agree that this should be just some simple scripting to get this done, which is why I'm so amazed it hasn't been done yet. 

I can plain english storyboard the desired code if you like: 

capture /dev/video0
name file using unix date code of seconds since birth.jpg
upload file via FTP
Wait 30 seconds and repeat

I'm sure someone could write this code faster than they could think of a cute animal to name their work after :)

Thanks again for any help you can offer,
eb

---

### Post by pastalavista on 2009-06-09
maybe [ZoneMinder]("http://www.zoneminder.com/")? It looks like it costs money but it's in my Synaptic

but why do you want to upload/store so many pics on your server?

---

### Post by Razmear on 2009-06-09
The output of 
date +%s  (seconds since 1970)
would provide a neat increasing unique number for each image. I'll have the file date stamps on the server to use for sorting later if needed. 

I plan on letting this app run constantly, then in the event of another theft at my house going to the server and getting the images to see who was in the house. This is why I don't want a chance of the filenames repeating and overwriting. In the event my server starts to fill up I'll just nuke the older files to make more space. 

--
Zoneminder would definitely work, but it's a bit of overkill for this older pc with 512 ram. I'd need a dedicated box for that app. 

eb

---

### Post by indiekid97 on 2009-06-09
Depending on the app your using to snap the picture (Cheese perhaps?), why not just have it snap every ~30 seconds using the command to take a picture (don't know it off the top of my head, google it) with cron by saving the command to a script and copying to /usr/local/bin as shown below

Then, set **rsync** to transfer the pictures from the save location to the server every half hour or so, like this
```
rsync -vz /save/location/here/*.jpg user@ipaddresshere:/server/location/here
#Delete Originals
rm -R /save/location/here 

```

Save that to /usr/local/bin as **movepicture.sh**
then,
```
sudo chmod 777 /usr/local/bin/movepicture.sh
```

Set that up to run at the right time with **cron**(check the man pages for instructions)

---

### Post by Razmear on 2009-06-09
Thanks for the tip indiekid, but it's still a bit over my head to implement your suggestion. 

the app webcamd is almost perfect, and it's written in Perl so it's human readable and hackable. webcamd will take a picture at whatever increment you choose and upload it via ftp to your server. The only problem is it overwrites the previous file each time only saving the latest image. It would seem that a simple hack by someone with a clue could change the filename from it's default to the output of date +%s.jpg which would make it perfect for my needs. 

The suggestion of uploading all the pics every half hour isn't a valid one as this is being setup to capture someone who may be breaking into my home and possibly would take this antique PC with them when they left. This is why I want the captured pics on my webhost and not locally stored. 

Thanks again for all the help so far,
eb

---

### Post by ChaoticXSinZ on 2009-06-10
Hey.

I was a somewhat bored so I decided to write this program. It's based on webcamd. It takes a picture a picture saves it as "snap-<timestamp>.png" and uploads to your ftp server. Configure ftp options.

```
#!/usr/bin/env perl
#*
#* LeXSnap v1.0.0
#* ~ Takes pictures using your webcam and uploads to an FTP server.
#*
#* Based on webcamd. <www.penguin-soft.com>
#*
#* Copyright (C) 2009  Luqman Aden <www.luqmanrocks.co.cc>.
#*
#* This program is free software: you can redistribute it and/or modify
#* it under the terms of the GNU General Public License as published by
#* the Free Software Foundation, either version 3 of the License, or
#* (at your option) any later version.
#*
#* This program is distributed in the hope that it will be useful,
#* but WITHOUT ANY WARRANTY; without even the implied warranty of
#* MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#* GNU General Public License for more details.

use POSIX;

use Image::Magick;
use Net::FTP;
	
my $userHome = $ENV{'HOME'};
my $LeXSnapHome = $userHome . "/.LeXSnap";

# Picture snap intervals
# In seconds
my $snapInterval = 5;

# FTP Host.
# i.e. ftp.somewhere.net
my $ftpHost = '';
	
# FTP Port
# Usually 21
my $ftpPort = '';
		
# FTP Username
my $ftpUser = '';
		
# FTP Password
my $ftpPass = '';
		
# FTP Directory for images
# Both trailing and leading slash please.
my $ftpIDir = '';
	
# FTP object
my $ftp;

sub main() {		
		
	dirsCheck();
	
	ftpCheck();
	
	argsCheck();
	
	my $action = $ARGV[0];
	
	if ($action eq "start") {
	
		# Check for LOCK file
		if (-e $LeXSnapHome . "/LeXSnap.lock") {
		
			print("LeXSnap already runnng!\n");
			
			exit;
		
		} else {
		
			print("LeXSnap started; Taking picture every $snapInterval second(s).\n");
			
			# Get rid of stop file if exists
			if (-e $LeXSnapHome . "/LeXSnap.stop") {
			
				system("rm -f $LeXSnapHome/LeXSnap.stop");
			
			}
			
			my $LOCK;
			
			open(LOCK, ">$LeXSnapHome/LeXSnap.lock");
			close(LOCK);
			
			fork && exit;
			
			while (1) {
			
				# Take picture
				my $snap = takePicture();
				
				# Add timestamp to image
				addTimestamp($snap);
				
				# Upload to FTP
				moveToFTP($snap);
				
				system("rm -f $snap");
			
				if (-e "$LeXSnapHome/LeXSnap.stop") {
				
					print("Got stop signal.\n");
				
				}
			
				# Stop if stop file found
				last if (-e "$LeXSnapHome/LeXSnap.stop");
				
				# Sleep
				sleep($snapInterval);
			
			}
			
			system("rm -f $LeXSnapHome/LeXSnap.stop");
			system("clear");
			exit 0;
		
		}
	
	} elsif ($action eq "stop") {
	
		if (-e "$LeXSnapHome/LeXSnap.stop") {
		
			print("LeXSnap has already been asked to stop, please wait.\n");
		
		} else {
		
			if (-e "$LeXSnapHome/LeXSnap.lock") {
			
				my $STOP;
			
				open(STOP, ">$LeXSnapHome/LeXSnap.stop");
				close(STOP);
				
				# Remove lock file
				system("rm -f $LeXSnapHome/LeXSnap.lock");
				
				print("Shutdown request issued to LeXSnap.\n");
			
			} else {
			
				print("LeXSnap is not running.\n");
			
			}
		
		}
	
	}
	
	return;
	
}

# Make needed dirs
sub dirsCheck() {

	# Create dir if not exists
	if (!(-e $LeXSnapHome)) {

		mkdir($LeXSnapHome);

	}
	
	# Create dir if not exists
	if (!(-e $LeXSnapHome . "/snaps/")) {

		mkdir($LeXSnapHome . "/snaps/");

	}

}

# Verify FTP details
sub ftpCheck() {

	$ftp = Net::FTP->new($ftpHost, Port => $ftpPort, Passive => 1) or die "LeXSnap: Can't connect to server: $@\n";
    $ftp->login($ftpUser, $ftpPass) or die "LeXSnap: Couldn't login. Check FTP details.\n";
    $ftp->cwd($ftpIDir) or die "LeXSnap: Couldn't change directory. Check FTP details.\n";

}

# Exits if poblem with arguments
sub argsCheck() {

	if ($ARGV[0] eq "") {

		print("Too few arguments!\n\n");

		print("LeXSnap v1.0.0\n");
		print("USAGE: LeXSnap.pl {start|stop}\n");
		
		exit;

	} elsif (defined($ARGV[1])) {
	
		print("Too many arguments!\n\n");
	
		print("LeXSnap v1.0.0\n");
		print("USAGE: LeXSnap.pl {start|stop}\n");
		
		exit;

	} elsif ($ARGV[0] ne "start" && $ARGV[0] ne "stop") {

		print("Unknown argument!\n\n");
	
		print("LeXSnap v1.0.0\n");
		print("USAGE: LeXSnap.pl {start|stop}\n");
		
		exit;
		
	}

}

# Function to add timestamp to image
sub addTimestamp($) {

	my($snap) = @_;

    my $image = Image::Magick->new(magick => 'PNG', font => 'clean');
    
    my $IMGDATA;
    
    open(IMGDATA, $snap);
    
    $image->Read(file => IMGDATA);
    
    close(IMGDATA);
    
    $image->Annotate(fill => 'white', pointsize => '14', text => "Timestamp: " . localtime() . strftime(" %Z", localtime()), gravity => "South", 'y' => '0');
    
    system("rm -f $snap");
    
    open(IMGDATA, ">$snap");
    
    $image->Write(file => IMGDATA, filename => $snap); 
    
    close(IMGDATA);

}

# Simple function for taking picture
sub takePicture() {

	print("Say cheese!\n");
	
	my $snap = $LeXSnapHome . "/snaps/snap-" . time . ".png";

	system("gst-launch-0.10 v4l2src ! ffmpegcolorspace ! pngenc ! filesink location='$snap'");
	
	return $snap;

}

# Function to upload image.
sub moveToFTP($) {

	my($snap) = @_;

    $ftp->binary();
    $ftp->put($snap) or die "LeXSnap: Couldn't upload \"$snap\".\n";

}

main();

exit 0;
```

Use LeXSnap.pl start and LeXSnap.pl stop.

EDIT: Added timestamp for images. Also removed strict and warnings as I can't seem to get it to work with that. [BTW: This is like my second commandline app written in perl. :P So it's good practise for me.]

Enjoy.

---

### Post by Razmear on 2009-06-10
Chaotic, you are a god!!! 

Thank You! 

I've got it up and running and feeding to:
[http://razmear.us/camfeed](http://razmear.us/camfeed) 
for now in case anyone wants to see the end result. 
You'll only see kinda dark pics of my monitor and such for now, but you can see the output files. 

How do you nominate a program for inclusion in Synaptic cuz this is the answer to many peoples requests as an improvement to webcamd.

Thanks again, You truly Rule! 
eb

edit: 
The cam is now pointed at my fishtank across the room. 
The two 0 byte files were generated when I was using Cheese to aim the cam, so don't expect your pics to upload if you are using a second application to access the video feed. No big deal, just something to look at if your using it and getting 0 byte files uploaded. 
Thanks again!
eb

---

### Post by Razmear on 2009-06-10
This is partially a bump for those who weren't around at 4am when the code was posted, and the other part is a question about the output. 

In the code snip:
```

# Simple function for taking picture
sub takePicture() {

	print("Say cheese!\n");
	
	my $snap = $LeXSnapHome . "/snaps/snap-" . time . ".png";

	system("gst-launch-0.10 v4l2src ! ffmpegcolorspace ! pngenc ! filesink location='$snap'");
	
	return $snap;

}

```

I can see where the .png encoding is called with 'pngenc', if I wanted to save a bit of disk space is there an equivalent code such as 'jpgenc' that will give me a bit better compression, and if so would I be seeing a performance hit on the pc due to the tighter encoding. 
Also, where are the default cam options stored for dev/video0 ? I'd like to tweak the brightness but not sure where to edit it so it sticks for this app. 

Thanks again for the code, 

eb

 (current average file size is about 300k so expecting 864mb per day of storage and 25.92gb of transfer volume per month).

---

### Post by Razmear on 2009-06-10
Just installed the updated script. Nice tweaks. 

Please keep us informed of any more improvements, this is a very useful and clean script, hope you keep practicing and turning out more stuff like this.

eb

---

### Post by e24ohm on 2009-07-13
> **indiekid97 said:**
> Depending on the app your using to snap the picture (Cheese perhaps?), why not just have it snap every ~30 seconds using the command to take a picture (don't know it off the top of my head, google it) with cron by saving the command to a script and copying to /usr/local/bin as shown below

Then, set **rsync** to transfer the pictures from the save location to the server every half hour or so, like this
```
rsync -vz /save/location/here/*.jpg user@ipaddresshere:/server/location/here
#Delete Originals
rm -R /save/location/here 

```

Save that to /usr/local/bin as **movepicture.sh**
then,
```
sudo chmod 777 /usr/local/bin/movepicture.sh
```

Set that up to run at the right time with **cron**(check the man pages for instructions)

hey what should the permissions be on the /usr/local/bin folder? I am getting an error when i try to move my script for another project over.
thanks - mate.


E

---

### Post by Gina on 2009-08-23
I've been trying ***webcamd*** but get an IO control error from the capture code line - from **v4lctl**.  So far I haven't found the reason.  I'll try Chaotic's capture alternative :)

I have command line app ***webcam*** working but would like to add extras to my website.  I use webcam for a weathercam on my weather website. [Link here]("http://ginad.org.uk/weather/Webcam.html")

---

