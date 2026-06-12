---
title: "DVDs don't play"
date: 2011-03-29
forum: Multimedia Software
---

### Post by Rocket J Squirrel on 2011-03-29
Ubuntu 10.10, Unity (netbook) version on dinky Acer Aspire One.

When I insert a music CD into the external (USB) optical drive ([ACER SDRW-08D 1 S-U]("http://www.netbooklink.com/accessories/optical-drives/asus-sdrw-08d1s-u-8x-slim-usb-2-0-external-dvd-writer-review")), I can play and rip CDs, no problem.

When I insert a DVD into the same drive, I can choose to launch either VLC Media Player or Movie Player. The disk spins up, whichever program I am using will find the title of the disk, but neither app plays the movie. The ">" button does nothing. 

After a bit, the disk spins down, I grow bored, and eject the disk. 

If anyone has some idea how to troubleshoot this, it would be welcome. We're taking this little netbook on a vacation and it would be nice to bring a couple of movies.

---

### Post by garvinrick4 on 2011-03-29
#This is in medibuntu repositories. Add them, if you do not how google medibuntu ubuntu.
```
sudo apt-get install libdvdcss2
```
Package: libdvdcss2                      
State: installed
Automatically installed: no
Version: 1.2.10-0.3medibuntu1
Priority: optional
Section: free/libs
Maintainer: Medibuntu Packaging Team <medibuntu-maintainers@lists.launchpad.net>
Uncompressed Size: 111 k
Depends: libc6 (>= 2.7)
Replaces: libdvdcss-dev (<= 0.0.3-3), libdvdcss0 (<= 1.0.0-0.0), libdvdcss2-dev
          (<= 1.2.10-0.0)
Provides: libdvdcss
Description: Simple foundation for reading DVDs - runtime libraries
 To allow applications to access some of the more advanced features of the DVD
 format.
Homepage: [http://download.videolan.org/](http://download.videolan.org/)

---

### Post by Rocket J Squirrel on 2011-03-29
Thank you. This is what I'm getting:

```
sudo apt-get install libdvdcss2
[sudo] password for jackelliott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libdvdcss2' has no installation candidate

```

WAIT -- I FORGOT TO INSTALL THE MEDIBUNTU REPOSITORY -- BE RIGHT BACK.

Hm, got an error with the command found at [https://help.ubuntu.com/community/Medibuntu:](https://help.ubuntu.com/community/Medibuntu:)

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

This is the error:

```
Err http://packages.medibuntu.org/ maverick/free medibuntu-keyring all 2008.04.20
  503  Service Temporarily Unavailable
Failed to fetch http://packages.medibuntu.org/pool/free/m/medibuntu-keyring/medibuntu-keyring_2008.04.20_all.deb  503  Service Temporarily Unavailable
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by n213978745 on 2011-03-29
In Ubuntu 10.10 with Gnome Desktop Environment, I do the following:

```
sudo apt-get install ubuntu-restricted-extras libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
```And now reboot your computer.

And if you are using a program called "Movie Player", do this also:
Open your "Movie Player", then "Edit" >> "Preference" >> check the "Disable deinterlacing of interlaced videos"

For some reason, in my computer I won't be able to play restricted dvd with this unchecked.

For more info:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by garvinrick4 on 2011-03-29
#Anything in a code box is copy and pasted into a terminal:

Have to install medibuntu repository and its key.
Copy and paste this below in a terminal:
Then copy and paste the line that starts with deb into your list on the bottom:
Change the maverick to what ever your version is. Now hit save in upper left and close:
```
gksudo gedit /etc/apt/sources.list
```deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick free non-free
```
wget --quiet http://packages.medibuntu.org/medibuntu-key.gpg -O - | sudo apt-key add - 
``````
sudo apt-get update
``````
sudo apt-get install libdvdcss2
```You have added medibuntu repository and its key to your sources.list
You have updated your sources.list
You have added libdvdcss2 which you need to view DVD's.

---

### Post by garvinrick4 on 2011-03-29
In my signature where it just says Main page -
If you click on it will give you instructions on how to install anything in you version
of Ubuntu.

---

### Post by Rocket J Squirrel on 2011-03-29
Wow -- a lot of responses, thanks guys. 

n213978745's response did the trick. VLC Media Player is now running just fine. 

"Movie Player" freezes on the intro then generates errors like "Connection Terminated", "pa_stream"cork() failed", "pa_stream_writeable_size() failed" and the like.

But as I say, VLC Media Player seems happy, so as far as I am concerned I am happy too. 

Unless there is a compelling reason to fix Movie Player.

---

### Post by n213978745 on 2011-03-29
> **Rocket J Squirrel said:**
> Wow -- a lot of responses, thanks guys. 

n213978745's response did the trick. VLC Media Player is now running just fine. 

"Movie Player" freezes on the intro then generates errors like "Connection Terminated", "pa_stream"cork() failed", "pa_stream_writeable_size() failed" and the like.

But as I say, VLC Media Player seems happy, so as far as I am concerned I am happy too. 

Unless there is a compelling reason to fix Movie Player.

Thank you for response, because a lot of people don't respond to thread once they got the answer :)  Also make sure to mark the thread [solve] in order to tell others that your thread has been solved.

As far as "Movie Player" goes, did you try what I suggest:
Open your "Movie Player", then "Edit" >> "Preference" >> check the "Disable deinterlacing of interlaced videos"

[IMG]http://img851.imageshack.us/img851/6587/screenshotyq.png[/IMG]

Because by default the "Movie Player" uncheck that box and enable the disinterlacing, which then has caused trouble when playing restricted DVD.

The only one compelling reason I can think of: is that you should ask yourself do you use all the feature in VLC, if not, the default "Movie Player" should work the best for you because it takes up less space -- which means it's less time for upgrade in future or possibly use less system resource.(somebody fixed me if I am wrong here)

---

### Post by Rocket J Squirrel on 2011-03-29
Hi garvinrick4,

Yes, I did disable the deinterlacing, and it made no difference. I should have mentioned that. Movie Player still packs up. 

As you say, MP has a smaller footprint than VLC, so of course I'd be interested to get it to work, but unless someone has some suggestions to debug the thing, VLC looks like the practical solution. 

Not quite marked "solved" here until we see if there's an easy way to fix MP. 

Thank you for your help.

---

### Post by mc4man on 2011-03-29
> here until we see if there's an easy way to fix MP.While there may or may not be easy way(s) to fix totem whem seeing those errors - the error message(s) are a bit generic, many posible causes, even more suggested 'fixes'

There are many current open bugs on this - 
 (have one myself though it is specific to  ac3 w/ 5.1 analog output in pulse (gstreamer pulseaudio plugin), have resolved by setting pulseaudio to 5.1 digital output
It was never an issue on a laptop which is only stereo output.

I would search the most common error message - "pa_stream_writeable_size() failed" and maybe you'll find a solution to your setup/use case.

( if you're _not using a surround sound system_ try removing the gstreamer0.10-pulseaudio package, if no change then re-install

---

### Post by garvinrick4 on 2011-03-29
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

libdvdread for Debian
---------------------

Many DVDs use CSS[0]. To play these discs, a special library is needed to decode
them, libdvdcss. Due to legal problems in some particular countries, Debian does
not distribute libdvdcss.

If it is legal for you to use CSS in your juristiction, you can:

  * Install the packages from <http://unofficial.debian-maintainers.org/>.

  * Manually download and compile the source code from
    <http://www.videolan.org/developers/libdvdcss.html>.

 [0] <http://en.wikipedia.org/wiki/Content_Scramble_System>

---

### Post by Rocket J Squirrel on 2011-03-29
Interesting reads, thanks for the links. 

Now that I have this netbook playing DVDs, I'm wondering if there is a straightforward way to rip DVDs we own onto the HD and play them from it, rather than lug along the little USB optical drive on our vacation?

---

### Post by collisionystm on 2011-03-29
sudo apt-get install ubuntu-restricted-extras

---

### Post by garvinrick4 on 2011-03-29
dvd::rip

---

### Post by collisionystm on 2011-03-29
dvd95 converter

---

### Post by Rocket J Squirrel on 2011-03-30
dvd95: can't find a install package.

dvd::rip -- I read that I need to add one of the following entries (depending on my distribution) to my /etc/apt/sources.list file:  [INDENT] deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sarge main deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) experimental main

[/INDENT]Which goes with 10.10?
collisonstym: what will "sudo apt-get install ubuntu-restricted-extras" do for me?

Thanks, guys.

---

### Post by garvinrick4 on 2011-03-30
dvd::rip, I just added in software center and stuck in a DVD and ripped it in chapters to /home
then copied it to a external in a directory I made. You need about 10 gig of free space to rip.
Pretty simple really. Screwed around with it for about a month got bored and went on to something else.

#Below is ubuntu-restricted-extras (should be first thing you install after setting up repo's.)
rick@rick-HP:~$ aptitude show ubuntu-restricted-extras (notice it is in multiverse repository)(check the box in Software Sources)
```
Package: ubuntu-restricted-extras        
State: installed
Automatically installed: no
Version: 43
Priority: optional
Section: multiverse/metapackages
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Uncompressed Size: 36.9 k
Depends: ubuntu-restricted-addons
Recommends: gstreamer0.10-plugins-ugly-multiverse, ttf-mscorefonts-installer,
            unrar, gstreamer0.10-plugins-bad-multiverse, libavcodec-extra-52,
            libmp4v2-0
Description: Commonly used restricted packages for Ubuntu
 This package depends on some commonly used packages in the Ubuntu multiverse
 repository. 
 
 Installing this package will pull in support for MP3 playback and decoding,
 support for various other audio formats (GStreamer plugins), Microsoft fonts,
 Java runtime environment, Flash plugin, LAME (to create compressed audio
 files), and DVD playback. 
 
 Please note that this does not install libdvdcss2, and will not let you play
 encrypted DVDs. For more information, see
 https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs 
 
 Please also note that packages from multiverse are restricted by copyright or
 legal issues in some countries. See http://www.ubuntu.com/ubuntu/licensing for
 more information.

rick@rick-HP:~$ 

```

---

### Post by Rocket J Squirrel on 2011-03-30
Thank you.

ubuntu-restricted-extras install no errors.

dvd::rip installed from Software Center no errors.

Set up Ubuntu to launch dvd:rip when dvd inserted into optical drive.

Inserted dvd, dvd:rip splash screen comes up, then fades, no evidence that dvd:rip is running. 
```
ps -e | grep dvd
``` shows nothing.

---

### Post by SeijiSensei on 2011-03-30
> **Rocket J Squirrel said:**
> Now that I have this netbook playing DVDs, I'm wondering if there is a straightforward way to rip DVDs we own onto the HD and play them from it, rather than lug along the little USB optical drive on our vacation?

Use **HandBrake**.  I added John Stebbins PPA to get the most recent versions:  [Releases]("https://launchpad.net/~stebbins/+archive/handbrake-releases") [Snapshots]("https://launchpad.net/~stebbins/+archive/handbrake-snapshots")  Being the adventurous sort, I'm using the snapshots.

---

### Post by Rocket J Squirrel on 2011-03-30
SeijiSensei: Handbrake installed easily and runs. Thank you.

Now, where can I find a tutorial about ripping dvds? Handbrake asked for the source, I pointed it to the dvd, and it showed two folders, VIDEO_TS and JACKET_P.

I figured the "movie" would be in the VIDEO_TS folder. When I opened it. I was presented with a buttload of .VOBs and other files. 

So what's the deal? Do you rip and transcode individual chapters, one at a time, then somehow stitch them together? Or is there a "one-click" method to rip the movie into one file that VLC Media Player can open and play?

A tutorial for the video-ignorant would be appreciated.

---

### Post by SeijiSensei on 2011-03-30
> **Rocket J Squirrel said:**
> Now, where can I find a tutorial about ripping dvds? Handbrake asked for the source, I pointed it to the dvd, and it showed two folders, VIDEO_TS and JACKET_P.

In the File menu on my copy, the DVD appears as a separate item below the Preferences line.  If I click that entry, Handbrake starts scanning the entire DVD to find chapters, etc. It will place the entire DVD into a single file unless you choose to break it up manually by selecting groups of chapters.

The Help menu offers a Guide option which will open the Guide in a browser window.

Remember I'm using the dailies; my version is HandBrake svn3887.  If you're using the release version, YMMV.

How cold is it up there in Frostbite Falls these days, Rocky?  Another couple of months until spring?  Oh, and give my regards to Gidney and Cloyd.  I wonder what Natasha Fatale would think of [Anna Chapman]("http://www.nypost.com/p/news/national/sexy_russian_spy_anna_chapman_2Zmmc1rSqu2H71x3v7BibM")?

---

### Post by JohnAStebbins on 2011-03-30
> **Rocket J Squirrel said:**
> SeijiSensei: Handbrake installed easily and runs. Thank you.

Now, where can I find a tutorial about ripping dvds? Handbrake asked for the source, I pointed it to the dvd, and it showed two folders, VIDEO_TS and JACKET_P.

I figured the "movie" would be in the VIDEO_TS folder. When I opened it. I was presented with a buttload of .VOBs and other files. 

So what's the deal? Do you rip and transcode individual chapters, one at a time, then somehow stitch them together? Or is there a "one-click" method to rip the movie into one file that VLC Media Player can open and play?

A tutorial for the video-ignorant would be appreciated.

For physical dvd's you can either open the device it is connected to (usually /dev/sr0) or you can open the top directory it is mounted on (e.g. /media/name-of-disc).  Opening the device or directory will scan the disc and populate the title combobox with a list of all the titles found on the disc.  Usually the main feature will automatically be selected in the combobox. But it's possible for detection to fail, so it's a good idea to check it. Once you've verified the title selection is correct, pick a preset on the right of the window, customize if needed, and press "Start".

---

### Post by Rocket J Squirrel on 2011-03-30
Thank you, all. 

Got it working, cracked the code: Handbrake is presently in the process of transcoding a dvd to an MP4. It's up to me now to see if the default settings give me what I want, etc. 

On this dinky Atom-powered netbook it looks like it will take a fair amount of time. I wish Handbrake had a progress bar. The "ghb" activity window is too tall for a netbook screen to see the bottommost entries, so can't tell what's going on, just what went on. 

But I've got a few weeks before our vacation to rip some dvds. 

SeijiSensei: Frostbite Falls is still a bit chilly this time of year. Gidney and Floyd, and Edgar and Chauncy were some of my favorite characters. 

I'm gonna mark this thread "solved," and if I run into some problems playing back the MP4, I'll start a new one.

Again, thanks, everyone!

---

### Post by JohnAStebbins on 2011-03-31
> **Rocket J Squirrel said:**
> On this dinky Atom-powered netbook it looks like it will take a fair amount of time. I wish Handbrake had a progress bar. The "ghb" activity window is too tall for a netbook screen to see the bottommost entries, so can't tell what's going on, just what went on. 
There is a progress bar off the bottom of your screen.  You might want to try this [https://wiki.kubuntu.org/X/Config/Resolution#Panning](https://wiki.kubuntu.org/X/Config/Resolution#Panning) viewport

---

### Post by Rocket J Squirrel on 2011-03-31
Hey JohnAStebbins,

Thanks!

Looks complicated.

I found a decent workaround: open the activity windown, do Ctrl-A, Ctrl-C open text editor, Ctrl-V and I can read all the details.

Less risky than installing that pan-round thing. No telling what kind of unintended havoc something like that could wreak. After all, if the screen goes black -- then what does a fellow do?

-- Jack

---

### Post by JohnAStebbins on 2011-04-01
> **Rocket J Squirrel said:**
> Hey JohnAStebbins,

Thanks!

Looks complicated.

I found a decent workaround: open the activity windown, do Ctrl-A, Ctrl-C open text editor, Ctrl-V and I can read all the details.

Less risky than installing that pan-round thing. No telling what kind of unintended havoc something like that could wreak. After all, if the screen goes black -- then what does a fellow do?

-- Jack
I understand your hesitation to fix what ain't broke.  But if you are ever feeling adventurous, the ability to pan around a larger virtual desktop is a real useful feature on those cramped netbook screens.

---

### Post by JedMeister on 2011-04-20
Try holding <Alt> and hold the left (mouse) button while the cursor is (anywhere) in the window you wish to move, then drag the window so you can see the bottom of it!

Easy and works a treat!

---

### Post by Rocket J Squirrel on 2011-04-20
Wow -- as if by magic! Thanks for the tip!

---

### Post by ellisblake on 2011-05-03
i have the same problem..
i cant play dvd in vlc and i followed these comands 
sudo apt-get install ubuntu-restricted-extras libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
 and everithing worked fine in the terminal until i got  this user agreement thing..


Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring ttf-mscorefonts-installer &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                                                                        &#9474; 
 &#9474;                                                                                                                          
 &#9474; 4. U.S. GOVERNMENT RESTRICTED RIGHTS. The SOFTWARE PRODUCT and documentation are provided with RESTRICTED RIGHTS.        
 &#9474; Use, duplication, or disclosure by the Government is subject to restrictions as set forth in subparagraph (c)(1)(ii)     
 &#9474; of the Rights in Technical Data and Computer Software clause at DFARS 252.227-7013 or subparagraphs (c) (1) and (2)      
 &#9474; of the Commercial Computer Software - Restricted Rights at 48 CFR 52.227-19, as applicable. Manufacturer is Microsoft    
 &#9474; Corporation/One Microsoft Way/Redmond, WA 98052-6399.                                                                    
 &#9474;                                                                                                                          
 &#9474; LIMITED WARRANTY                                                                                                         
 &#9474;                                                                                                                          
 &#9474; NO WARRANTIES. Microsoft expressly disclaims any warranty for the SOFTWARE PRODUCT. The SOFTWARE PRODUCT and any         
 &#9474; related documentation is provided "as is" without warranty of any kind, either express or implied, including, without    
 &#9474; limitation, the implied warranties or merchantability, fitness for a particular purpose, or noninfringement. The         
 &#9474; entire risk arising out of use or performance of the SOFTWARE PRODUCT remains with you.                                  
 &#9474;                                                                                                                          
 &#9474; NO LIABILITY FOR CONSEQUENTIAL DAMAGES. In no event shall Microsoft or its suppliers be liable for any damages           
 &#9474; whatsoever (including, without limitation, damages for loss of business profits, business interruption, loss of          
 &#9474; business information, or any other pecuniary loss) arising out of the use of or inability to use this Microsoft          
 &#9474; product, even if Microsoft has been advised of the possibility of such damages. Because some states/jurisdictions do     
 &#9474; not allow the exclusion or limitation of liability for consequential or incidental damages, the above limitation may     
 &#9474; not apply to you.                                                                                                        
 &#9474;                                                                                                                          
 &#9474; MISCELLANEOUS                                                                                                            
 &#9474;                                                                                                                          
 &#9474; If you acquired this product in the United States, this EULA is governed by the laws of the State of Washington.         
 &#9474;                                                                                                                          
 &#9474; If this product was acquired outside the United States, then local laws may apply.                                       
 &#9474;                                                                                                                          
 &#9474; Should you have any questions concerning this EULA, or if you desire to contact Microsoft for any reason, please         
 &#9474; contact the Microsoft subsidiary serving your country, or write: Microsoft Sales Information Center/One Microsoft        
 &#9474; Way/Redmond, WA 98052-6399.                                                                                              
 &#9474;                                                                                                                          
 &#9474;                                                                                                                          
 &#9474;                                                         <Ok>                                                             
 &#9474;                                                                                                                        &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                                                                            

but i dont know what to do now ..i triedt to press ok or enter but nothing happens....i dont know what to do...if i try to close the terminal it tells me that there is a process running and if i close the terminal i will kill it...

please help.///

---

