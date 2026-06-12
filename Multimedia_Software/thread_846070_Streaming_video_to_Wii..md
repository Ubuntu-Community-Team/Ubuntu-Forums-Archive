---
title: "Streaming video to Wii."
date: 2008-07-01
forum: Multimedia Software
---

### Post by Kromgol on 2008-07-01
Hey all,

As i use Ubuntu now, i'm trying to find something that makes Linux stream some of my videos etc. to the Wii, so i can watch it there on the Opera browser.

I've already checked out WiiCR, but i couldn't get it to work as i didn't understand some of the instructions.. If you could help me, i would be glad.

[http://wmc.sourceforge.net/wiki/index.php/Install](http://wmc.sourceforge.net/wiki/index.php/Install)

Look at the *nix part there, and check out 2 and 4, i really can't find the executable in the archive i've downloaded, maybe i will need to compile the programs first ?

---

### Post by adam_kimber on 2008-07-01
From what I can see step 1 is to install the packages for XAMPP. However unless the WII streaming program requires the latest version of mencoder I am not sure why you couldn't just install mencoder from the repository (i think that comes with the mplayer package) and use that binary in the instructions. Locate mencoder should give the location of wher it is and then copy it as per the instructions.

---

### Post by Kromgol on 2008-07-01
I think i've found it in /usr/bin , i will try and see if it's correct.

EDIT: In the instructions it says that i need to start enc_daemon.pl , i made it executable and then runned ./enc_daemon.pl in the terminal from the directory, but then it says this: 

: the command was not found (Poor translation from swedish to english :P, kommandot hittades inte is the same as this)
: kommandot hittades inte
: kommandot hittades inte
: kommandot hittades inte 
./enc_daemon.pl: line 12: use: kommandot hittades inte
: kommandot hittades inte 
./enc_daemon.pl: line 13: syntax error near unexpected token `('
'/enc_daemon.pl: line 13: `STDOUT->autoflush(1);

The file contains this:

```
# encoding daemon



# written by jacob jarick for the WiiCR project.



# license = gpl

# author = jacob jarick, [email]mem.namefix@gmail.com[/email] , mem on #wiidev @ efnet



# ===============================================================================================================================================================

# vars and libs

# ===============================================================================================================================================================



use IO::Handle;

STDOUT->autoflush(1);



our $dir = $0;



$dir =~ s/\\/\//g;

if($dir =~ /\//)

{

	$dir =~ s/^(.*)\/(.*?)$/$1/;

}

else

{

	$dir = cwd();

}



do "$dir/subs.pm";

do "$dir/config.pl" or die "ERROR: !! couldnt load $dir/config.pl";

#&set_global_vars;



$version = "0.4.3";



# ===============================================================================================================================================================

# main

# ===============================================================================================================================================================



if(!-d $flv_local_dir)

{

	print "\n\n!!! ERROR: \$flv_local_dir = \"$flv_local_dir\"\n___ \$flv_local_dir does not exist or the path is incorrect recheck your config.dat.\n\n\n>>> enc_daemon will exit in 10 seconds.";

	sleep 10;

	exit 0;

}



print "\n\n>>> WiiCR Encode Daemon $version Starting\n\n";



chdir $work_dir;



$c = 0;

while ()

{

	$c++;

	opendir(DIR, "$work_dir") or die "\n\n\n\>>> ERROR: couldnt open: $work_dir\n___ Check that your path is correct and check that work directory exists (if it doesnt create it).";

	@dir = readdir(DIR);

	close(DIR);

	

	if($c == 1)

	{

		print ">>> WiiCR Encode Daemon $version running, waiting for jobs\n\n";

	}

	for (@dir)

	{

		if($_ =~ /\.(bat|sh)$/i)

		{

			print "\n\n>>> Found job \"$_\" , executing\n";

			system("$sys_shell $_");

			print "\n>>> Deleting $_\n";

			unlink("$_");

			print ">>> Done\n\n";

			last;

		}

	}

	sleep 2;

	print ".";

}
```

---

### Post by Kromgol on 2008-07-01
I would really, really appreciate a fast answer as i want this setuped and done as fast as possible :P

---

### Post by Kromgol on 2008-07-04
Anyone? :(

---

### Post by adam_kimber on 2008-07-04
Sorry about the delay but as I have not got this installed I have not been able to work out your problem. I will try installing it myself tonight. It might be a bug in the coding or something else..... 

PS do you run 32bit or 64bit?

---

### Post by Kromgol on 2008-07-05
> **adam_kimber said:**
> Sorry about the delay but as I have not got this installed I have not been able to work out your problem. I will try installing it myself tonight. It might be a bug in the coding or something else..... 

PS do you run 32bit or 64bit?

I run 32bit.

---

### Post by adam_kimber on 2008-07-05
Hi this is what I did.

1) [Get XAMPP Source]("http://www.apachefriends.org/en/xampp-linux.html#374") as there are no packages as far as I can see.

2) Installed XAMPP using this command ```
sudo tar xvfz xampp-linux-1.6.6.tar.gz -C /opt
```

3) Tested XAMPP by typing ```
sudo /opt/lampp/lampp start
``` and by going to ```
http://localhost/
``` got a nice page something a bit like [this]("http://www.apachefriends.org/images/380.jpg") 

4) <install both flv and mencoder packages>

5) The next part is a little meh in the instructions. What they mean is to create a directory called /opt/lampp/wiicr_tools. I did this by ```
sudo mkdir /opt/lampp/wiicr_tools
```

5) Use the following commands to copy the flvtool2 and mencoder binaries to the wiicr_tools directory 
```
sudo cp /usr/bin/mencoder /opt/lampp/wiicr_tools/
```
```
sudo cp /usr/bin/flvtool2 /opt/lampp/wiicr_tools/
```

6) Extract the WiiCR folder, by either unrar or using archive manager. 

7) Go to that directory (mine was on my desktop so ```
cd ~/Desktop/WiiCR_0.3.2_RC6
``` and copy the files to the /opt/lampp/ by the following method ```
sudo cp -r * /opt/lampp/
```

8) Edit the config file ```
 sudo gedit /opt/lampp/htdocs/wiicr/config.dat 
```

9) Change to this ```



##################


# WiiCR settings #


##################





theme		= icons1


flvtool_exe	= /opt/lampp/wiicr_tools/flvtool2


use_flvtool	= off


enc_exe		= /opt/lampp/wiicr_tools/mencoder


enc_opts	= -ofps 24 -of lavf -oac mp3lame -lameopts abr:br=64 -srate 22050 -ovc lavc -lavfopts i_certify_that_my_video_stream_does_not_use_b_frames -lavcopts vcodec=flv:keyint=50:vbitrate=300:mbd=2:mv0:trell:v4mv:cbp:last_pred=3 -vf scale=480:348


duration	= 300


#drive_list	= c: m: y: z:





########################


# OS Specific settings #


########################





xampp_dir	= /opt/lampp


perl_exe	= /opt/lampp/wiicr_tools/perl


sys_shell	= /usr/bin/bash





```

10) Run test.pl to see if server is running properly. Go to a web browser at [http://localhost/wiicr/test.pl](http://localhost/wiicr/test.pl). If you get a 404 the standard version of ubuntus apache is running. ```
sudo /etc/init.d/apache2 stop
``` wil sort that. Then start/restart lampp. (lampp has its own embedded apache server rather than the ubuntu inbuilt one)

This is where I got stuck. I cannot seem to get past the internal server error 500. It is something to so with this perl script and the inbuilt security of perl methinks. Though I am unsure of what the actual root problem might be... 

Sorry if this is vague.... :( 

Perl is working but not properly on this lampp setup. The index.pl should be displaying automatically but not plus I am getting these internal server errors. :confused:

---

### Post by Kromgol on 2008-07-06
> **adam_kimber said:**
> Hi this is what I did.

1) [Get XAMPP Source]("http://www.apachefriends.org/en/xampp-linux.html#374") as there are no packages as far as I can see.

2) Installed XAMPP using this command ```
sudo tar xvfz xampp-linux-1.6.6.tar.gz -C /opt
```

3) Tested XAMPP by typing ```
sudo /opt/lampp/lampp start
``` and by going to ```
http://localhost/
``` got a nice page something a bit like [this]("http://www.apachefriends.org/images/380.jpg") 

4) <install both flv and mencoder packages>

5) The next part is a little meh in the instructions. What they mean is to create a directory called /opt/lampp/wiicr_tools. I did this by ```
sudo mkdir /opt/lampp/wiicr_tools
```

5) Use the following commands to copy the flvtool2 and mencoder binaries to the wiicr_tools directory 
```
sudo cp /usr/bin/mencoder /opt/lampp/wiicr_tools/
```
```
sudo cp /usr/bin/flvtool2 /opt/lampp/wiicr_tools/
```

6) Extract the WiiCR folder, by either unrar or using archive manager. 

7) Go to that directory (mine was on my desktop so ```
cd ~/Desktop/WiiCR_0.3.2_RC6
``` and copy the files to the /opt/lampp/ by the following method ```
sudo cp -r * /opt/lampp/
```

8) Edit the config file ```
 sudo gedit /opt/lampp/htdocs/wiicr/config.dat 
```

9) Change to this ```



##################


# WiiCR settings #


##################





theme		= icons1


flvtool_exe	= /opt/lampp/wiicr_tools/flvtool2


use_flvtool	= off


enc_exe		= /opt/lampp/wiicr_tools/mencoder


enc_opts	= -ofps 24 -of lavf -oac mp3lame -lameopts abr:br=64 -srate 22050 -ovc lavc -lavfopts i_certify_that_my_video_stream_does_not_use_b_frames -lavcopts vcodec=flv:keyint=50:vbitrate=300:mbd=2:mv0:trell:v4mv:cbp:last_pred=3 -vf scale=480:348


duration	= 300


#drive_list	= c: m: y: z:





########################


# OS Specific settings #


########################





xampp_dir	= /opt/lampp


perl_exe	= /opt/lampp/wiicr_tools/perl


sys_shell	= /usr/bin/bash





```

10) Run test.pl to see if server is running properly. Go to a web browser at [http://localhost/wiicr/test.pl](http://localhost/wiicr/test.pl). If you get a 404 the standard version of ubuntus apache is running. ```
sudo /etc/init.d/apache2 stop
``` wil sort that. Then start/restart lampp. (lampp has its own embedded apache server rather than the ubuntu inbuilt one)

This is where I got stuck. I cannot seem to get past the internal server error 500. It is something to so with this perl script and the inbuilt security of perl methinks. Though I am unsure of what the actual root problem might be... 

Sorry if this is vague.... :( 

Perl is working but not properly on this lampp setup. The index.pl should be displaying automatically but not plus I am getting these internal server errors. :confused:

Seems like you did what i did too, i got that Server error too.

Oh well, if nobody has any clue, then i think i will pass on WiiCR :(

---

### Post by adam_kimber on 2008-07-07
You could try the following sites? 
[http://www.redkawa.com/mediacenters/wiimediacenterx/]("http://www.redkawa.com/mediacenters/wiimediacenterx/")
[http://www.last100.com/2007/06/25/five-resources-to-create-a-wii-media-center/]("http://www.last100.com/2007/06/25/five-resources-to-create-a-wii-media-center/")

The full hog. :D 

[http://www.wiili.org/index.php/Main_Page]("http://www.wiili.org/index.php/Main_Page")

---

### Post by Kromgol on 2008-07-08
Thanks! Seems pretty nice.

---

