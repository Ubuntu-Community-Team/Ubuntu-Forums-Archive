---
title: "Mythbuntu 12.04 64bit (0.25) Failed Install - BUGS found"
date: 2012-05-30
forum: Mythbuntu
---

### Post by nhtrader on 2012-05-30
This weekend I tried to install MythTV and have numerous problems.

So I decided to document the BUGS encountered.


BUGS found during CD installation of Mythbuntu 12.04 64bit (v0.25),

Prompt choices selected...
1. checked - 3rd party MP3 decoding; unchecked - download updates
2. selected other option so that I could specify use entire HDD for mount point /
3. enabled format option (clean wipe)
4. selected Locale
5. selected English
6. successful install - reboot prompt appears.

After reboot FE appears.
1. First problem, Mouse invisible but appears when accidently moved over textboxes.
2. The installation prompted me for language already. Why didn't the user information propagate? Why isn't english set as default?  (default: DANSK, AFAR)
3. Select Appearance Menu and FINISH. But it bounces out, 2 levels. Now back to SETUP not previous Menu. DID 'Qt painter' fail? Was an error generated?
4. Select Audio Menu. The page with the option "use Internal Volum Controls" is enabled but box contents are invisible. SOLN: uncheck and check, then contents appear.
5. Select Video Menu. then Playback Menu. page 3/8 contents invisible.
6. Select Video Menu. then Recording Priorities. make changes; FINISH. re-enter and changes not saved.
7. Select Video Menu. then Media setttings. default paths set here vary. Why? One install will generate /home/user/.mythtv/... While on another new clean install (using same install CD), this path can be /var/lib/mythtv/....
		Why do PATHs vary depending on user responses to installation prompts? Plus, why aren't the group permissions set to mythtv user group in default path: /home/user/.mythtv
8. Select Video Menu. then Artwork and DataSources. <ESC> key inactive. Press <ESC> and no exit possible. Must use CANCEL or OK buttons. Is this an "Inconsistent GUI" or indicative of another internal problem.
9. Now exit FE and System Error Message is waiting for me.
	ExecPath = /usr/share/mythtv/metadata/tmb3.py
	pkg      = mythtv-common 2:0.25.0+fixes.201...
	crashed with import error /usr/lib/python2.7/dist....
	traceback= .var.log.mythtv.myavtest.log  and .var.log.mythbackend.log
10. Now in desktop; "Update Manager" prompts me for updates. I decline updates b/c in previous attempts to install these updates get stuck when applying changes to samba - system hangs.

11. Now if attempt to reenter FE, I get stuck in endless loop.
Why isn't there a button to "exit to desktop" (aka Kill switch)? Cancel button is useless. This would improve the user experience. At least the program could get the user back to the desktop so that they could hunt down a user guide / help menu / troubleshoot.
Secondly, why isn't there a prompt to ask the user if they want to change the permissions to allow them write access? Then the program can either proceed or exit to desktop. Plus, this prompt could show the user the offending event which would help in diagnosing the problem (identify to user the filename; pathname; program action that failed, etc.)

Then I must use ALT+F11 to access Applications Menu and select Accessories|Terminal so that I can kill offending processes.
Use commands
sudo su
ps aux|grep myth (not mythtv, b/c it could be mythfrontend or mythtv-setup)
find 2 offending processes and kill both (note: the order is important ex: kill 1000; kill 1001; not kill 1001; kill 1000)

now I changed permissions to /home/user/.mythtv to include in mythtv group
sudo su
chown user:mythtv /home/user/.mythtv
exit
(BTW, this is the first time I tried to change the group permissions with the hope that it might work. But it didn't change the outcome. Still in endless loops. Yes, I've done a few clean installs b/c I'm trying to help with the progress of development by identifying these BUGs.)

12. now run Applications|System|MythTV Backend Setup
Immediately noticed the mouse works perfectly. Why doesn't it work in FE like is does in BE? This is an inconsistent GUI experience.
make changes, but now stuck in endless loop
Why isn't there a button to "exit to desktop" (aka Kill switch)? Cancel button is useless. This would improve the user experience. At least the program could get the user back to the desktop so that they could hunt down a user guide / help menu / troubleshoot.
Secondly, why isn't there a prompt to ask the user if they want to change the permissions to allow them write access? Then the program can either proceed or exit to desktop. Plus, this prompt could show the user the offending event which would help in diagnosing the problem (identify to user the filename; pathname; program action that failed, etc.)

Then I must use ALT+F11 to access Applications Menu and select Accessories|Terminal so that I can kill offending processes.
Use commands
sudo su
ps aux|grep myth
finds 5 processes and kill 3 processes with "mythtv-setup" in numerical order (lowest PID first)

Lastly, the sum of all of these BUGS doesn't make it easy to diagnose what is wrong and where to begin. A newbie is now hopelessly thrown into the hackers world of endless hours of research and frustration. 

I haven't even started the process of debugging issues associated with TV tuner capture cards. This is still not easy.

---

### Post by tgm4883 on 2012-05-30
> **nhtrader said:**
> This weekend I tried to install MythTV and have numerous problems.

So I decided to document the BUGS encountered.


BUGS found during CD installation of Mythbuntu 12.04 64bit (v0.25),

Prompt choices selected...
1. checked - 3rd party MP3 decoding; unchecked - download updates
2. selected other option so that I could specify use entire HDD for mount point /
3. enabled format option (clean wipe)
4. selected Locale
5. selected English
6. successful install - reboot prompt appears.

<snip>

I stopped reading at this point as you 

A) Haven't told us everything you selected in the installer (eg. Is this a Frontend Only install?)
B) What machine specs? CPU, RAM, Video card, etc. Proprietary drivers installed?
C) Did you really install without SWAP? (points to B)
D) Don't seem to have linked to any of the bug reports that you submitted ( I don't see any when searching)

---

### Post by anonymousdog on 2012-05-30
It's pretty clear from his process that it's a combined FE/BE.

I'm pretty sure MOST users aren't really comfortable filing bug reports.  The process is intimidating, and that intimidation is often compounded by defensive response(s) to the bug reports.  I think that most users are far more comfortable with these forums and may be seeking encouragement to file bug reports once initial (but often unconfirmed, uneducated, uncertain) suspicions of a bug  are confirmed by more experienced users here.

As far as the "bugs":

I've NOT seen the locale bug -- i.e., initial MythTV FE config screen have locale pre-selected in my experience.

Mouse behavior in MythTV is always a little flaky, and it is probably not part of the UI intent to support mouse interaction with a system designed to run from a remote control at 8ft or more distance from the screen.

I've also never seen the Audio bug, but, honestly wouldn't think much about it if I did -- these kinds of issues are extremely typical across software AND platforms.

Recording priorities: did these changes get saved on second attempt?  Ever?

Video Metadata paths: "Why do PATHs vary depending on user responses to installation prompts?"...Are you sure that's what you meant?!, why would you expect user answers NOT to impact the results?  What choices impacted the paths (results)?  Group permissions on these paths don't need to include mythtv because they are for the FE (which runs in user context), not the BE (which runs as a service in mythtv user context).  MythTV was intended to be an appliance with (primarily) a single-user automatically logged on; if you want shared metadata paths for multiple users, you'll have to do the (minimal) configuration to allow that.  IIRC, the user's home directory is the default.

Artwork and DataSources: the Escape key works for me.  This may have been fixed in an update.  You must be using a different menu layout from 'default' as this item is not a sub-menu of Video for my installations.

Declining updates globally because of an issue with one package is self-defeating.  You really need to the updates in order to meaningfully debug since you'll lose credibility trying to debug an old release (in a fast-changing release landscape).  You can always decline just the samba updates.  Also, on a fresh installation, with no special samba config, hanging on reconfig of samba would seem to indicate another (possibly hardware) problem.

Yes, crash recovery works against you if you have a persistent configuration issue that causes a reliable crash.  Some UI method for breaking out of crash recovery WOULD be good.

---

### Post by nhtrader on 2012-05-30
> **tgm4883 said:**
> I stopped reading at this point as you 

A) Haven't told us everything you selected in the installer (eg. Is this a Frontend Only install?)
B) What machine specs? CPU, RAM, Video card, etc. Proprietary drivers installed?
C) Did you really install without SWAP? (points to B)
D) Don't seem to have linked to any of the bug reports that you submitted ( I don't see any when searching)


Glad you asked.

A. Primary Frontend/Backend install
     selected all 4 services: SSH, Samba, NFS, Mythtv Service.

D. Bug reporting fails whenever I attempt to use it.

C. A swap is cited in the list I see. This swap is listed under /dev/sda1 in the partioning portion of the installation process.  But can I admit that I didn't specify one. 

But when I perform df from terminal mode:
/dev/sda1      728162252 13406136 678310832   2% /
udev             1723964        4   1723960   1% /dev
tmpfs             706292     1064    705228   1% /run
none                5120        0      5120   0% /run/lock
none             1765724      132   1765592   1% /run/shm


I can add that I also installed MythTV using the "ERASE ALL DATA" option (choice #2 Erase Existing 12.04 not #3-Something Else). And got the same results.

B. 
CPU AMD Athlon II X2 245
DRAM DDR2 4 Gb
SATA 3.0 HDD 750Gb
M/B GA-MA785GM-US2H/GA-MA785GM-US2H, BIOS F7 11/30/2009
using onboard graphics.
SAMSUNG  DVDWBD SH-B083L, SB00, max UDMA/100
Tv Capture Card Hauppauge HVR-1250

No proprietary drivers installed yet. I couldn't get to Mythbuntu Control Centre to install AMD/ATI FLGRX driver. BTW I get a choice of two. the post-installation versions fails to install. The other version works in previous installation attempts. But it was not installed as of this report. 

This report describes what I did and when I did it. Just putting it out there.

---

### Post by nhtrader on 2012-05-30
I an attempt to isolate the "update manager" hanging problem I did the following.

Another fresh clean install. Same conditions with only one change:
I enabled USB & Serial Remote LIRC
for Hauppauge TV Card
enabled Generate dynamic utton mapping
enabled Generate frontend restart mapping

After I reboot into FE I exit to desktop
Open Update Manager only to close it (took notice of number of pkgs to be updated = 84)

Open terminal mode
sudo su
apt-get upgrade
yes
now when it reaches samba-common it doesn't hang.
It prompts me to choose a version of samba.conf. I choose original (Keep Original: Mythbuntu's copy)
and update proceeds to completion without error.

Then I return to desktop.

Then I open Update Manager again only to find 6 more updates related to: Complete Generic Linux Kernel 3.2.0-24-generic

Click Install. Proceeds to successful completion. Reboot.

Here I am. At this point I at least have a fully updated 12.04 system, but I still can't use MythTV.

BUG: The problem is that the GUI implementation of Update Manager fails to propagate these samba prompts to the user, which causes the system to hang.

---

### Post by nickrout on 2012-05-30
I for one didn't have any of these problems on install.

Appearance menu has always taken back to the main menu when finished, as far back as I can remember in mythtv.

Mythtv is not designed to be used with a mouse, so forgetaboutit,

Alt-Tab will usually take you out of a full screen myth gui, or whatever button opens your applications menu (ctrl-esc previously, may be alt-f11 now).

Gui inconsistencies are nothing to do with mythbuntu, nor are many of your other perceived faults. Mythtv developers do not generally hang out here.

I have found sometimes parts of the setup gui go blank, i think it is both theme dependent and renderer dependent (coupled with what video card/driver you are using). You haven't actually told us what graphics chip/driver you are using, merely that it is built into the motherboard. Are we supposed to google that for you?

I assume it is some ATi thing, and if it doesn't work properly, that would be par for the course. Go nvidia if you want the best from your HTPC.

df will not show swap space, mount will. cfdisk will show what your partitioning looks like.

So you have to choose your locale in mythtv, it's not difficult and is a one off choice.

I assume you are aware that the version of mythtv in 12.04 should be upgraded to 0.25-fixes.

But frankly if you believe you have genuine bugs, file them with launchpad for ubuntu and trac for mythtv.

---

### Post by nhtrader on 2012-05-30
After Another new install, I confirmed that changing the password crashed MythTV.

Here's what I did.
Selected English. The I selected "you may wish to update Installer". Waited; then the notice disappeared.

Next prompt:
unchecked-download updates
unchecked-3rd party MP3 (Fluendo MP3)

Next prompt:
selected choice #2 - Erase Ubuntu 12.04 & reinstall.
selected NY
selected english
selected Primary Backend with Frontend on same PC
selected 4 services (SSH, Samba, NFS, Mythtv)
Selected USB & Serial LIRC

BUG: clicked on dropbox:
now dropbox expands to veritcal length of monitor and top half is blank.
dropbox is not populated above the textbox display position, but it populates as user scrolls down.
 
selected Hauppauge TV Card
checked-Generate dynamic mapping
checked-Generate frontend restart mapping

Install reaches endpoint - reboot

After reboot, FE appears using Black mythbuntu theme 25.12
press esc and exit.

Open update manager blinking on desktop.
note: 89 updates.
close update manager - did not install updates.

open terminal
sudo su
apt-get upgrade
samba prompt: select "keep original copy" (mythbuntu's samba.conf)
upgrade proceeds to successful completion.

chown -R user:mythtv /home/user/.mythtv
chown -R user:mythtv /home/user/.lirc

(note: symbolic links are still user:user not user:mythtv)

exit terminal
open GUI update manager and install 6 remaining updates (generic linux kernel 3.2.0-24-generic)
reboot.

After reboot, FE starts
select English, English, <E>, FINISH
Now FE exits! MythTV is working as expected. 
Exit FE

(note: did not change database name, username, or password; no database changes were made.)


Now enter terminal mode as user not root:

$mythtv-setup

I can make changes and changes are saved

exit to terminal mode

(The Language and Country screen does not appear! NO LOOPING! System is working as expected.)

Now I make changes so that the system will connect properly to my Hauppauge TV Capture Card HVR-1250.
Why the system can't handle this card without hacking it, is in my opinion another BUG?

sudo su
create file:
pico /etc/modprobe.d/cx32885.conf
add line: options cx23885 card=19
save and exit
reboot


Now reenter FE

BUG: changed password, proceed to next page select FINISH
now stuck in endless loop.

Must use ALT+F11 to view Menubar. Select Applications|Terminal
sudo su
ps aux|grep myth
kill 2 mythfrontend processes in numerical order low to high

exit sudo su
Back to user terminal mode,
inserted these commands

$mysql -u root -p

mysql>GRANT ALL PRIVILEGES ON mythconverg.* TO 'mythtv'@"localhost" identified by "password here" WITH GRANT OPTION;
mysql>GRANT ALL PRIVILEGES ON mythconverg.* TO 'mythtv'@"%" identified by "password here" WITH GRANT OPTION;
mysql>use mysql;
mysql>UPDATE user SET Password=PASSWORD('password here') WHERE user='mythtv';
mysql>FLUSH PRIVILEGES;
mysql>exit

Open GUI MythTV Backend Setup
make changes. Everything responds normally. NO MORE ENDLESS LOOPING.
exit BE

Open GUI FrontEnd
FE is working. NO MORE ENDLESS LOOPING>

go to Appearance, now English is default.
go to Setup|Media Settings|Video Settings|General Settings
now paths = /var/lib/mythtv....

All changes made are saved.

I now have a fully updated and functioning Ubuntu 12.04 running MythTV v0.25+fixes without any proprietary drivers.

Now the only difference for me, between v0.23, v0.24, and v0.25 is that FE in v0.25 now uses "OpenGL High Quality" in "Playback Menu" rather than simply "High Quality" (which was required for me in v0.23, v0.24)

Summary:
Why is changing the password still such a NO-NO?
Why isn't there a prompt that warns the user that changing the password will be problematic?
Why is the password in the FE, if the user doesn't have the right to change it?
Why not program it such that the user can see it but can't change it? Why put it in a textbox when changing it mucks up the system?

Now think about how many issues are related to this one change. It's no wonder that newbies get stymied. Who would think that one simple password change would blow up the system? Changing a password is so elementary that beyond reproach. It's obvious, it must be something else. And we all go the rabbit hole of trial and error.

Did you notice that the PATHs are now different? /home/user/.mythtv is a symptom of a problem. /var/lib/mythtv implies the database is connected.
If DANSK is the default language, this is a symptom of a problem. If the system is connected to the database, then the proper language appears as the default.
If changes can't be saved, this is another symptom.

Here's another scenario. If the user changes the hostname, then another problem sets in. The user will not be able to use the command mysql -u root -p b/c they will get an access denied error. And they won't be to make any changes particularly if MYSQL's "skip-networking" option is active (only 127.0.0.1 can connect). Now the newbie has really screwed this up. 

Now add to this the fact that the system is inoperable and they don't have a user manual, or more importantly, access to their webbrowser b/c the system is broken.

---

### Post by nhtrader on 2012-05-30
BUG: new password fails to propagate

Found another orphaned file that has contains the original password:

/etc/apache2/sites-available/mythweb.conf


As you can guess, I'm working on fixing MythWeb.

---

### Post by anonymousdog on 2012-05-31
> **nhtrader said:**
> After Another new install, I confirmed that changing the password crashed MythTV.
You may have established that, but you really are going to enrage some staff with this post; you have thrown around "bug" quite a bit where it does not belong and held the entire, absolutely free, operating system and software package to an unfair standard.

> **nhtrader said:**
> Here's what I did.
...
unchecked-download updates
I would not make that choice since it just makes things more complex...everything that follows until the capture card items.

> **nhtrader said:**
> 
BUG: clicked on dropbox:
now dropbox expands to veritcal length of monitor and top half is blank.
dropbox is not populated above the textbox display position, but it populates as user scrolls down.
This is, at most, a purely cosmetic bug only present in the installer.

> **nhtrader said:**
> 
Open update manager blinking on desktop.
note: 89 updates.
close update manager - did not install updates.
If you would expand the lower section of update manager when it pauses for the samba.conf question, you will see the question and be able to respond.  That totally obviates the terminal-based process below.  All this could be avoided by allowing updates to download during the installation.

> **nhtrader said:**
> 
open terminal
sudo su
apt-get upgrade

This process is not needed, but if you execute 'apt-get dist-upgrade', the second update process using Update Manager would not be necessary (even if you chose to allow updates to download during the installation).
> **nhtrader said:**
> 
samba prompt: select "keep original copy" (mythbuntu's samba.conf)

This is only necessary b/c you didn't dl updates during install.  Any answer to the question would be fine since you haven't configured samba yet.

> **nhtrader said:**
> 
chown -R user:mythtv /home/user/.mythtv
chown -R user:mythtv /home/user/.lirc

Not necessary or desired.

> **nhtrader said:**
> 
$mythtv-setup

I can make changes and changes are saved

Why launch setup manually?  This is exactly the same as launching through the UI.

> **nhtrader said:**
> 
Now I make changes so that the system will connect properly to my Hauppauge TV Capture Card HVR-1250.
Why the system can't handle this card without hacking it, is in my opinion another BUG?
I'm picking up on your frustration, but you're blaming the victim here (and you know it).  Since you have the solution here, you've obviously seen the thread which explains why this happens; it is a manufacturer issue where different hardware identifies itself as the same.  There is no way to accommodate that in code since the hardware is lying to the O/S. 

> **nhtrader said:**
> Now reenter FE

BUG: changed password, proceed to next page select FINISH
now stuck in endless loop.

Um, Yes.  You broke it.  The password was correct and set before you changed it.

> **nhtrader said:**
> Summary:
Why is changing the password still such a NO-NO?
It's a design and priorities choice, and it's not a "no no", it's just not in the UI -- you found the methods easily enough, right?  Please feel free to submit patches.
> **nhtrader said:**
> Why isn't there a prompt that warns the user that changing the password will be problematic?
That's probably a good suggestion for the MythTV project.
> **nhtrader said:**
> Why is the password in the FE, if the user doesn't have the right to change it?
Because a remote FE setup won't have the proper password pre-populated; so, there was a priority on getting it in the UI.
> **nhtrader said:**
> 
Why not program it such that the user can see it but can't change it? Why put it in a textbox when changing it mucks up the system?
Also, probably a good suggestion but would require significant reworking of the MythTV setup UI and underlying code...not a Mythbuntu task.  Feel free to suggest this to the MythTV project.

> **nhtrader said:**
> Now think about how many issues are related to this one change. It's no wonder that newbies get stymied. Who would think that one simple password change would blow up the system? Changing a password is so elementary that beyond reproach. It's obvious, it must be something else. And we all go the rabbit hole of trial and error.
In computers, if you go mucking about with working systems, you need to be prepared to revert changes (and not have so many that you cannot).  If you alter a vanilla installation of most anything and have an expectation of that strategy reliably yielding properly working software, you are going to be continually disappointed.  That applies equally for OSS and proprietary software.  A more reasonable approach is to take the vanilla installation, ensure it works, then tweak and test in increments; you don't have to like it, but it just the way it's done.

"beyond reproach" is harsh, overly passionate, not supported, and won't yield you any sympathy among the developers or experienced staffers who might otherwise try to help you out.

> **nhtrader said:**
> 
Here's another scenario. If the user changes the hostname, then another problem sets in. The user will not be able to use the command mysql -u root -p b/c they will get an access denied error. And they won't be to make any changes particularly if MYSQL's "skip-networking" option is active (only 127.0.0.1 can connect). Now the newbie has really screwed this up.
Wow.  Ok, MythTV and Mythbuntu are meant for applicances, not general use PCs.  It is not in the core intent of the project(s) to produce a PC where indiscriminate changes can be made without consequence.  If you want to step outside "the box", well, "there be dragons there".  Again, this would be the same for ANY computer system with complex, client/server software hosted on it.

> **nhtrader said:**
> Now add to this the fact that the system is inoperable and they don't have a user manual, or more importantly, access to their webbrowser b/c the system is broken.
They could still boot their PC from the same disk from they installed, get a working system to browse the web, and/or restart the installation.

---

### Post by anonymousdog on 2012-05-31
> **nhtrader said:**
> BUG: new password fails to propagate

Found another orphaned file that has contains the original password:

/etc/apache2/sites-available/mythweb.conf


There is no failure to propagate, the file is not orphaned, and it's certainly not a bug.  You have hit a shortcoming that could develop into a feature request (if you don't treat it like some totally predictable and fatal failure).

Mythweb is just another FE. You changed the SQL password on the BE.  Then you changed it on the FE.  Now you have to change it in Mythweb, another FE.

I don't know with certainty, but my guess would be that a 'dpkg-reconfigure mythweb' would fix it anyway.

---

### Post by nickrout on 2012-05-31
> **nhtrader said:**
> BUG: new password fails to propagate

Found another orphaned file that has contains the original password:

/etc/apache2/sites-available/mythweb.conf


As you can guess, I'm working on fixing MythWeb.

perhaps you'd be happier with a windows solution. (Not that there is a windows system to challenge myth's functionality)

---

### Post by tgm4883 on 2012-05-31
As previous posters have suggested, changing the password incorrectly and your inexperience with MythTV have caused most of your perceived issues. Other problems due to incorrect hardware identification are an issue as well, although not your fault. At least you incorrectly blamed the distro as a whole and not just the 64-bit version.

Since you have reinstalled many times and keep experiencing issues (such as bug filing crashes), you may want to verify the MD5SUM of the ISO you downloaded and make sure it isn't corrupt. Oh and while you are doing that, you may want to download the release version of 12.04 from [http://www.mythbuntu.org/downloads](http://www.mythbuntu.org/downloads) as the only time I've ever seen the following message is from the beta or before images.

> **nhtrader said:**
> 
Here's what I did.
Selected English. The I selected "you may wish to update Installer". Waited; then the notice disappeared.


:EDIT:

Oh, and please stop throwing around the word Bug like you think you know what it means. Just because something doesn't work as you would expect or you can't figure something out (or you broke it) doesn't mean it is a bug.

---

### Post by nhtrader on 2012-05-31
UNFRIENDLY BEHAVIOR: when you are forced to use ALT+F11, b/c <ESC> becomes inactive, and you right click the task "Frontend" and select close. "Frontend" restarts itself and doesn't close.


This is an inconsistent behavior with the knowledge leveraged by the user from the linux GUI. If a user elects to close a task, the task is "killed". 

MythTV 's response is to restart. I see that Myth has been designed for "self-healing"/recovery/restart. And if the software fails on its own and recovers, I'm impressed as an "end-user" (us stupid people). But when I choose to shut it down, and it restarts. 

This is inconsistent behavior within the constraints of the GUI. This a separate event, and the software should recognize it. And of course if it is by design that the user shouldn't "touch" this, then design it so that the user can't see it. Which will it be?

Note, the user selected close not restart.

---

### Post by nhtrader on 2012-05-31
> **tgm4883 said:**
> As previous posters have suggested, changing the password incorrectly and your inexperience with MythTV have caused most of your perceived issues. Other problems due to incorrect hardware identification are an issue as well, although not your fault. At least you incorrectly blamed the distro as a whole and not just the 64-bit version.

Since you have reinstalled many times and keep experiencing issues (such as bug filing crashes), you may want to verify the MD5SUM of the ISO you downloaded and make sure it isn't corrupt. Oh and while you are doing that, you may want to download the release version of 12.04 from [http://www.mythbuntu.org/downloads](http://www.mythbuntu.org/downloads) as the only time I've ever seen the following message is from the beta or before images.



:EDIT:

Oh, and please stop throwing around the word Bug like you think you know what it means. Just because something doesn't work as you would expect or you can't figure something out (or you broke it) doesn't mean it is a bug.

Thanks for bringing this up. I did in indeed perform the MD5SUM verification and the version I downloaded was directly from the Mythbuntu.org Website on May 7, 2012. 


I will refrain from the word.

But I will suggest, that you consider that "stress" testing software is a common practice in the development world. And as a lowly end user, all I'm doing is exploring the parameters that you all have designed in to the package. If I'm not allowed to touch it, then why is it there. And if touching it will bring disaster, why not warn the user with a message box? I see message boxes for silly warnings (a newer version of the theme is here).

Whether you want to blame me for "breaking it" or not is irrelevant. The fact is these events described expose the weaknesses that currently exist. In a world moving fast towards smartphones and tablets. Developers see the mantra - make it easy. Push button apps only underscore that users have grown tired of searching the knowledge base for answers. They want to leverage their knowledge of the GUI and have software respond as expected.

As a user I take full responsibility for reading all documentation. But unfortunately, docs are not updated with each new version. For instance, where is it stated that there are newer playback modes available in v0.25 along with an description of what the value of each one is? So as an end user, you force me to explore through trial and error. And if along the way, I "break" something... 

Well, please understand that these inconsistencies should be vetted for the sake of transparency. Because in the end, this knowledge is both good for us users and for you developers.

Stress testing software is not taboo.

---

### Post by tgm4883 on 2012-05-31
> **nhtrader said:**
> Thanks for bringing this up. I did in indeed perform the MD5SUM verification and the version I downloaded was directly from the Mythbuntu.org Website on May 7, 2012. 


I will refrain from the word.

But I will suggest, that you consider that "stress" testing software is a common practice in the development world. And as a lowly end user, all I'm doing is exploring the parameters that you all have designed in to the package. If I'm not allowed to touch it, then why is it there. And if touching it will bring disaster, why not warn the user with a message box? I see message boxes for silly warnings (a newer version of the theme is here).

Whether you want to blame me for "breaking it" or not is irrelevant. The fact is these events described expose the weaknesses that currently exist. In a world moving fast towards smartphones and tablets. Developers see the mantra - make it easy. Push button apps only underscore that users have grown tired of searching the knowledge base for answers. They want to leverage their knowledge of the GUI and have software respond as expected.

As a user I take full responsibility for reading all documentation. But unfortunately, docs are not updated with each new version. For instance, where is it stated that there are newer playback modes available in v0.25 along with an description of what the value of each one is? So as an end user, you force me to explore through trial and error. And if along the way, I "break" something... 

Well, please understand that these inconsistencies should be vetted for the sake of transparency. Because in the end, this knowledge is both good for us users and for you developers.

Stress testing software is not taboo.

First things first. Please post the output of the MD5SUM that you got when you checked the CD. I'd like the computed value of the ISO you downloaded, not the value from the website.

You are the only case where I've seen this many issues. Most users simply install, configure and use MythTV happily. This has nothing to do with stress testing and not catching bugs. Mostly this is because for some reason you thought it a good idea to change the password, and then wonder why it won't automatically authenticate in a bunch of different locations.

To answer your question "if you aren't allowed to touch it, then why is it there". Simple answer, because some people like to alter some of the settings or have some other custom configuration they need to work with. People are allowed to touch it because they know what they are doing with those settings, it is obvious that you do not. So you see something and immediately decide to mess with it? I would surely hate to be your mechanic.

And I do get to blame you for breaking it. I get to blame you for breaking it because that is exactly what you did. Had you clicked something or done something a "normal" user would have done and it broke I would consider that a bug, but you didn't. You logged directly into the database and ran a SQL query to change the password. Let it be known that is under no uncertain terms, completely unsupported. Because you wandered outside of what most normal users would do, there is a bit of an expectation that you at least half-way know what you are doing. That is why there isn't any Vistaesqe UAC pop up warning you of every change you are trying to make.

Regarding the documentation, yes it could use help in some areas. I suppose that is why the documentation is a wiki that anyone can add to and update. As a developer for Mythbuntu (and not MythTV) I have not contributed a single line of code to MythTV (not directly anyway). So in terms of capability to write documentation, we are on equal footing as we are both users. I urge you to continue to test and  find the issues you are having, then seek out help to figure out why it is doing that. Once you understand the issue, go to the wiki and write some documentation about it. You can write documentation on the MythTV wiki, or if you prefer a Question/Answer approach, you can write it at [AskUbuntu.com]("http://askubuntu.com/questions/tagged/mythbuntu"). They are fine with you asking and answering your own questions, providing it stays in a question/answer format.

Unfortunately what is more likely to happen is you will say you will add to the documentation once you learn and have used MythTV a bit more. You might even make some minor changes to it in the near future. But in roughly 2 weeks, you'll stop making changes (if you had even made any) and the documentation will be left up to the developers to maintain. Now I agree that they should contribute to documentation (and they do, a lot), but I think that documentation also needs to come from user experiences, and who better to do that than a user. I'm not saying this because I don't believe you want to help, I'm saying this because a few times each year someone feels the need to complain about the documentation. We let them know they are able to contribute themselves, they say they will, and within a few weeks they are never heard from again. It is a recurring trend and has been a few months since the last one, so we are probably due.

---

### Post by anonymousdog on 2012-05-31
> **nhtrader said:**
> But I will suggest, that you consider that "stress" testing software is a common practice in the development world. And as a lowly end user, all I'm doing is exploring the parameters that you all have designed in to the package. If I'm not allowed to touch it, then why is it there. And if touching it will bring disaster, why not warn the user with a message box? I see message boxes for silly warnings (a newer version of the theme is here).
I'm not sure of the correct term for the type of testing you're doing, but it's not stress testing.  Stress testing loads a system to the point of failure; it is not a process of trying to explore all configuration options to see whether the system can be broken via mis/re-configuration.  Moreover, if you're testing, you expect failure that may not be considered a bug; you don't expect things to continue working since the point of stress testing is to break the system with load.  You ARE allowed to touch "it" but should expect that deviations from the vanilla package will require planning and configuration testing *before* expecting successful deployment

Also, I already suggested it would be good to have a warning about changing a working MySQL password.  Please submit that and any other MythTV suggestions to the MythTV project...but, please, stop returning to it here since it's unproductive and a source of irritation to those that might help you.

> **nhtrader said:**
> 
Whether you want to blame me for "breaking it" or not is irrelevant.
"Blame" was not at issue there.  My appropriately attributing the breakage to your misconfiguration was intended to highlight its not being a "bug".

> **nhtrader said:**
> The fact is these events described expose the weaknesses that currently exist. In a world moving fast towards smartphones and tablets. Developers see the mantra - make it easy. Push button apps only underscore that users have grown tired of searching the knowledge base for answers. They want to leverage their knowledge of the GUI and have software respond as expected.

You keep returning to this idea that you are serving some greater purpose in self-appointing to be a "stress tester" for MythTV, then reporting problems to another project.  (If you want to contribute, ask the MythTV team to do so as a "stress tester" or report issues them.)

Your "make it easy" is an unfair/impossible standard for complex client/server systems, especially those developed in an OSS environment, especially where the product is 100% free.  This is an essential difference between "apps" and "applications", especially client/server systems with broad feature sets.  I know of *zero* client/server systems with large feature sets that also conform to your "make it easy" rubric.  On the other hand, my Mythdroid MythTV remote control "app" for Android "just works", but it has a limited feature set and is not expandable to accommodate a larger feature set.

Other packages like XBMC may be more to your liking if you're looking for a simpler setup (and lesser/different functionality).

> **nhtrader said:**
> As a user I take full responsibility for reading all documentation. But unfortunately, docs are not updated with each new version. For instance, where is it stated that there are newer playback modes available in v0.25 along with an description of what the value of each one is? So as an end user, you force me to explore through trial and error. And if along the way, I "break" something... 
...then, undo the change and get on with your day.  If you're testing, you expect some changes to break things, and you have to be prepared to revert them.  This is also a point I addressed above; let's, please, not perseverate on it.

I agree that documentation is spotty; feel free to contribute some.  IIRC, the MythTV project did post changes in playback modes with OpenGL modes getting a total rewrite.

> **nhtrader said:**
> Well, please understand that these inconsistencies should be vetted for the sake of transparency. Because in the end, this knowledge is both good for us users and for you developers.
I still want to stress that the *only* real issue you have uncovered is the preference to disable change in and/or warn about change of the FE MySQL password.

> **nhtrader said:**
> Stress testing software is not taboo.
...but that's not what you're doing, and this is the wrong venue for it.  That needs to be done within development modalities of the responsible project, MythTV.  Even if the Mythbuntu team were responsible for MythTV development, this would *still* not be the appropriate venue for the results of development testing.  The Mythbuntu team is responsible for creating the integrated installer, the Mythbuntu Control Center and other packages that make installing MythTV on top of xfce/Ubuntu and single-pass, integrated process.  Issues re: MythTV itself really should be directed back to that project through the tools by which they expect that information to be submitted.

---

### Post by Kr0nZ on 2012-05-31
> **tgm4883 said:**
> ...
you may want to download the release version of 12.04 from [http://www.mythbuntu.org/downloads](http://www.mythbuntu.org/downloads) as the only time I've ever seen the following message is from the beta or before images.

'Originally Posted by nhtrader
Here's what I did.
Selected English. The I selected "you may wish to update Installer". Waited; then the notice disappeared.'
...

I downloaded Mythbuntu 12.04 last weekend and I got this message, I clicked it but never had any issues with my install.

OP: I dont understand why your taking such a customized approach to installing mythbuntu, if your hardware doesnt work that understandable but why go changing the password unless you really know what you doing? when your go messing with default settings you should always remeber how to revert.

From a fresh install without changing anything what problems are you having exactly?
Its hard to diagnose whats wrong when you changed so many things.
I for one have never had to change any folder permissions, in my home dir my '.mythtv' dir is user:user, and it works no problems.

are you sure your not confusing 'mythtv/.mythtv' with 'user/.mythtv'?
The BE runs under the mythtv user not your username. The FE runs under your username.

My Install approach to mythbuntu is something like:
- Boot from USB, and select install.
- Select download updates, and 3rd party drivers.
- Configure options such as name and languages etc.
- Whenever upgrading asks about configuration files I always keep local copy.
- After installing boot into mythbuntu.
- Open mythbuntu control panel.
- Make such the Nvidia proprietary drivers are installing.
- Enable mythbuntu updates repo.
- Open teminal
- Run apt-get update, apt-get upgrade.
- - Again keeping local configuration files if asked.
- Run dmesg to make sure all my drivers have been detected
- (I normal have to copy firmware to /lib/firmware)
- After verifying drivers such as TV tuner, Sound, and video works I start 'mythtv backend setup' from the menu and run through the options like I normally would.
-
- After checking that mythfrontend and backend are working as expected, I then apply custom changes (such as manually restore recording schedules in mysql).

---

### Post by nhtrader on 2012-05-31
> **Kr0nZ said:**
> 
are you sure your not confusing 'mythtv/.mythtv' with 'user/.mythtv'?
The BE runs under the mythtv user not your username. The FE runs under your username.


For clarity, user/.mythtv is generic for public consumption. It could be bob/.mythtv, or reba/.mythtv - not mythtv/.mythtv

---

### Post by anonymousdog on 2012-05-31
> **Kr0nZ said:**
> 
I for one have never had to change any folder permissions, in my home dir my '.mythtv' dir is user:user, and it works no problems.

are you sure your not confusing 'mythtv/.mythtv' with 'user/.mythtv'?


> **nhtrader said:**
> For clarity, user/.mythtv is generic for public consumption. It could be bob/.mythtv, or reba/.mythtv - not mythtv/.mythtv

I don't think Kr0nZ was confused; he was suggesting a reason why you came to the erroneous conclusion that the mythtv group needs ownership of ~/.mythtv in the primary user's home directory.

---

### Post by Kr0nZ on 2012-05-31
> **nhtrader said:**
> For clarity, user/.mythtv is generic for public consumption. It could be bob/.mythtv, or reba/.mythtv - not mythtv/.mythtv

Yes I am aware of that, in my case 'user' is 'htpc',
but are you aware that there is a secondary user account and home folder called 'mythtv'?
this is the user that the mythtv BE runs under.

---

### Post by tgm4883 on 2012-05-31
> **Kr0nZ said:**
> Yes I am aware of that, in my case 'user' is 'htpc',
but are you aware that there is a secondary user account and home folder called 'mythtv'?
this is the user that the mythtv BE runs under.

But the backend doesn't need access to anything in it's home directory, nor does the backend need access to anything in your home directory. This is why, as other people have pointed out, that it is not necessary to change the ownership of the .mythtv directory to the mythtv group.

---

### Post by nhtrader on 2012-05-31
> **anonymousdog said:**
> 
...but that's not what you're doing, and this is the wrong venue for it.  That needs to be done within development modalities of the responsible project, MythTV.  Even if the Mythbuntu team were responsible for MythTV development, this would *still* not be the appropriate venue for the results of development testing.  The Mythbuntu team is responsible for creating the integrated installer, the Mythbuntu Control Center and other packages that make installing MythTV on top of xfce/Ubuntu and single-pass, integrated process.  Issues re: MythTV itself really should be directed back to that project through the tools by which they expect that information to be submitted.

Then I must apologize.

As tagged by Kronz, I am OP. I am "studip". I don't know about the fiefdoms that reign. All I know is that I use a mythtbuntu installation CD. In my mind, I didn't separate the various factions. This is my ignorance. And I do apologize for the misplacement of this thread and therefore the original title of the thread. I have stricken from the annuals of time and better yet google's search engine.

Should you wish to erase this thread, it is fine by me. (Notice I renamed it.)

I would whole heartedly like to direct my experiences to the appropriate teams. I don't know any better, and I've been schooled.


Is it fair to say that the "disappearing" "update this installer" pertains to the mythbuntu team? (BTW, should I assume that it was updated since the notice disappeared?)

Is the half filled drop down box a mythbuntu issue?

The rest of my issues are certainly with MythTV. Right?

During the installation process I am prompted to select a Remote Control. I make my choices, and yet they don't appear in "Mythbuntu Control Centre". Which team handles that?

Which team do I ask for help, if I didn't select an option but now post-installation would like to enable it (fluendo MP3)?

I am all too glad to learn new things. And I know that I am not an expert, and I am more than happy to admit when I'm wrong. I've accused the wrong team, and I am sorry.

I now understand that Mythbuntu and MythTV are separate teams. But I still don't understand whose domain is what.

---

### Post by Kr0nZ on 2012-05-31
> **nhtrader said:**
> 
if I didn't select an option but now post-installation would like to enable it (fluendo MP3)?

in a terminal type
```
sudo apt-get install gstreamer0.10-fluendo-mp3
```

or search for 'gstreamer0.10-fluendo-mp3' in the software center.


You can asked anywhere for help about problems you have, but be sure that something is actually a bug before you start saying such.

---

