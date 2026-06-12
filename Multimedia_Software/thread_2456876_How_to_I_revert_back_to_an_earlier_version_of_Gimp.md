---
title: "How to I revert back to an earlier version of Gimp -EXIF data problem with latest ver"
date: 2021-01-21
forum: Multimedia Software
---

### Post by jmichaels29 on 2021-01-21
I'm having this EXIF data problem with the latest version of Gimp using a Pentax camera.  

See:  [https://www.gimpusers.com/forums/gimp-user/20941-pentax-exif-data-stripped).](https://www.gimpusers.com/forums/gimp-user/20941-pentax-exif-data-stripped).)[FONT=&amp]Also see: [https://gitlab.gnome.org/GNOME/gimp/-/issues/2253](https://gitlab.gnome.org/GNOME/gimp/-/issues/2253)

I would like to go back to [COLOR=#212124][FONT=&amp]GIMP 2.8.22 (or even [/FONT][/COLOR][/FONT][COLOR=#212124][FONT=&amp]GIMP 2.8.16)[/FONT][/COLOR][FONT=&amp][COLOR=#212124][FONT=&amp]

How do I do this and also keep Ubuntu from updating Gimp to latest version during a software update..[/FONT][/COLOR][/FONT]

---

### Post by Paddy Landau on 2021-01-21
The first link that you gave is incorrect. Here's the [corrected link]("https://www.gimpusers.com/forums/gimp-user/20941-pentax-exif-data-stripped").

Unfortunately, it seems that the only way to [install an older version]("https://www.gimp.org/downloads/oldstable/") is to uninstall the version that you have, [download the source code]("https://download.gimp.org/mirror/pub/gimp/v2.8/"), and follow the instructions to [compile it yourself]("https://www.gimp.org/source/").

That'll be a hassle, so if you're uncomfortable with doing that, you might have to stick with the workaround described in the link that you gave until GIMP is fixed.

---

### Post by jmichaels29 on 2021-01-21
> **Paddy Landau said:**
> The first link that you gave is incorrect. Here's the [corrected link]("https://www.gimpusers.com/forums/gimp-user/20941-pentax-exif-data-stripped").

Unfortunately, it seems that the only way to [install an older version]("https://www.gimp.org/downloads/oldstable/") is to uninstall the version that you have, [download the source code]("https://download.gimp.org/mirror/pub/gimp/v2.8/"), and follow the instructions to [compile it yourself]("https://www.gimp.org/source/").

That'll be a hassle, so if you're uncomfortable with doing that, you might have to stick with the workaround described in the link that you gave until GIMP is fixed.


Thanks for correcting my dead link.

Instead of reverting to an older version of Gimp, I installed the "unstable" Beta version (2.99.4) which has the issue fixed.

I am curious how my Ubuntu automatic software updates will handle this Beta version - will it perhaps try to upgrade it to the latest stable released version in "Ubuntu Software" ?    Should I attempt to put a "freeze" on the beta version?

---

### Post by Dennis N on 2021-01-21
> I am curious how my Ubuntu automatic software updates will handle this Beta version

It depends how the beta was packaged. If you used the Flatpak development repository on Flathub that Gimp suggests on the download page, then it will update automatically if you have Gnome Software installed along with gnome-software-plugin-flatpak. These updates through Gnome Software would be only to a newer Flatpak development version.

---

### Post by jmichaels29 on 2021-01-21
> **Dennis N said:**
> It depends how the beta was packaged. If you used the Flatpak development repository on Flathub that Gimp suggests on the download page, then it will update automatically if you have Gnome Software installed along with gnome-software-plugin-flatpak. These updates through Gnome Software would be only to a newer Flatpak development version.

Hmmm, the beta version (2.99.4) I installed is likely going to be a "more recent" version of Gimp than even the next stable version that is released. I wonder what it will do.

fyi: The Ubuntu Software "center" does not even recognize that I have the Gimp beta installed when I search for "Gimp." - it simply offers me the current stable version (2.10.22) to be installed.

Question:  How could I see how the beta was packaged with a command line?

---

### Post by Paddy Landau on 2021-01-22
> **jmichaels29 said:**
> Instead of reverting to an older version of Gimp, I installed the "unstable" Beta version (2.99.4) which has the issue fixed.
Good to know. Once the fix makes its way into the stable release, I would advise removing the beta version and installing the stable release, unless you're happy to continue to test the beta version.
> **jmichaels29 said:**
> I am curious how my Ubuntu automatic software updates will handle this Beta version…
The automatic updates won't downgrade your installed version. They might upgrade to a later beta version, depending on how you installed it.
> **jmichaels29 said:**
> Should I attempt to put a "freeze" on the beta version?
That might be possible, again depending on how you installed it.
> **jmichaels29 said:**
> fyi: The Ubuntu Software "center" does not even recognize that I have the Gimp beta installed when I search for "Gimp."…
Again, that depends on how you installed it.

Something to note is that the Ubuntu Software Store is incomplete, and doesn't recognise snaps and flatpaks. I advise that you uninstall the Ubuntu Software Store, and replace it with the Gnome Software Store, which is complete. I described the [correct way in a post]("https://ubuntuforums.org/showthread.php?t=2456751&p=14015237#post14015237") on an unrelated thread.
> **jmichaels29 said:**
> Question:  How could I see how the beta was packaged with a command line?
Again, that depends on how you installed it. Tell us exactly how you installed the beta version, and we can answer this.

---

### Post by Dennis N on 2021-01-22
> **jmichaels29 said:**
> Hmmm, the beta version (2.99.4) I installed is likely going to be a "more recent" version of Gimp than even the next stable version that is released. I wonder what it will do.

fyi: The Ubuntu Software "center" does not even recognize that I have the Gimp beta installed when I search for "Gimp." - it simply offers me the current stable version (2.10.22) to be installed.

Question:  How could I see how the beta was packaged with a command line?

If the Flatpaks works like the Snaps, you stay in the same branch* that you installed from - in your case, the beta repo, I think. Snaps however will automatically change to the stable channel when there are no updates within a certain length of time. I don't know if that's true about Flatpaks.

Ubuntu Software does not update Flatpaks. You need to install Gnome Software + the flatpak plugin, and uninstall Ubuntu Software to keep the Flatpak apps updated, or update them from the command line: **flatpak update**. 

**flatpak list --app** will display all flatpak applications you installed. My set of Flatpaks, all in the stable branch.

```
dmn@Sydney:~$ flatpak list --app
Name                   Application ID              Version Branch Installation
Blanket                com.rafaelmardojai.Blanket  0.3.1   stable system
ghostwriter            &#8230;hub.wereturtle.ghostwriter 1.8.0   stable system
Bluefish               nl.openoffice.bluefish      2.2.10  stable system
GNU Image Manipulatio&#8230; org.gimp.GIMP               2.10.22 stable system
GNOME Maps             org.gnome.Maps              3.38.1  stable system
Quadrapassel           org.gnome.Quadrapassel      3.38    stable system
Meld                   org.gnome.meld              3.20.2  stable system
Inkscape               org.inkscape.Inkscape       1.0.2   stable system
Kate                   org.kde.kate                20.12.1 stable system
KBlocks                org.kde.kblocks             20.12.1 stable system
Krita                  org.kde.krita               4.4.2   stable system
Okular                 org.kde.okular              1.11.3  stable system
LibreOffice            org.libreoffice.LibreOffice 7.0.4.2 stable system
Stellarium             org.stellarium.Stellarium   0.20.4  stable system

``` 

* the corresponding Snap terminology is "channel".

---

### Post by jmichaels29 on 2021-01-22
> **Paddy Landau said:**
> 
Again, that depends on how you installed it. Tell us exactly how you installed the beta version, and we can answer this.

Flatpak
michael@michael-HP-EliteDesk-800-G1-SFF:~$ flatpak list --app
Name                            Application ID  Version  Branch  Installation
GNU Image Manipulation Program  org.gimp.GIMP   2.99.4   beta    user

But if I check packages installed, this gimp data does pop up (even though it's not installed in Ubuntu software center)

[edited]
michael@michael-HP-EliteDesk-800-G1-SFF:~$ apt list --installed
gimp-data/focal,focal,now 2.10.18-1 all [installed,automatic]

or

michael@michael-HP-EliteDesk-800-G1-SFF:~$ apt -qq list gimp
gimp/focal 2.10.18-1 amd64

---

### Post by Dennis N on 2021-01-22
```
michael@michael-HP-EliteDesk-800-G1-SFF:~$ apt list --installed
gimp-data/focal,focal,now 2.10.18-1 all [installed,automatic]

```
**apt** is only a package manager for .deb packages, so doesn't show any flatpaks in the listing.
**flatpak** is the package manager for Flatpak packages.

Note: for Flatpaks, you can leave out the --app option when listing, and see the supporting packages (called runtimes) as well. 
**flatpak --help** will show all the possible options you can use with the flatpak command.

---

### Post by Paddy Landau on 2021-01-22
To add to what @Dennis N said, to see all packages, you'd need three commands:
```
apt list --installed 'gimp*'  # Display all packages installed with DEB.
flatpak list | fgrep gimp     # Display all packages installed with flatpak.
snap list | fgrep gimp        # Display all packages installed with snap.
```
Alternatively, if you've followed the [instructions that I referenced]("https://ubuntuforums.org/showthread.php?t=2456751&p=14015237#post14015237") in my [earlier post]("https://ubuntuforums.org/showthread.php?t=2456876&p=14016049&viewfull=1#post14016049"), you can just use Gnome Software Store to view all three types of packages.

---

### Post by DuckHook on 2021-01-22
If you are game for some complexity, you can always run older apps (or, at the other end of the scale, unstable bleeding edge development versions) by firing up a container and installing the app inside of that.  Many use Docker. I use LXD. If interested in the latter, follow the instructions in my sig: Sandboxing Apps with LXD. The older GIMP version you want would be the default in an older Ubuntu version like 18.04.

ALERT: Winding road ahead.

I won't claim that containers are easy, but they are very versatile and don't drag in the bloat that any of the snap/flatpak/appimage technologies tend to do.

---

### Post by jmichaels29 on 2021-01-22
> **Paddy Landau said:**
> To add to what @Dennis N said, to see all packages, you'd need three commands:
```
apt list --installed 'gimp*'  # Display all packages installed with DEB.
flatpak list | fgrep gimp     # Display all packages installed with flatpak.
snap list | fgrep gimp        # Display all packages installed with snap.
```
Alternatively, if you've followed the [instructions that I referenced]("https://ubuntuforums.org/showthread.php?t=2456751&p=14015237#post14015237") in my [earlier post]("https://ubuntuforums.org/showthread.php?t=2456876&p=14016049&viewfull=1#post14016049"), you can just use Gnome Software Store to view all three types of packages.

```
michael@michael-HP-EliteDesk-800-G1-SFF:~$ apt list --installed 'gimp*'
Listing... Done
gimp-data/focal,focal,now 2.10.18-1 all [installed,automatic]
michael@michael-HP-EliteDesk-800-G1-SFF:~$ flatpak list | fgrep gimp
GNU Image Manipulation Program    org.gimp.GIMP    2.99.4    beta    flathub-beta    user
michael@michael-HP-EliteDesk-800-G1-SFF:~$ snap list | fgrep gimp 
michael@michael-HP-EliteDesk-800-G1-SFF:~$
```

I'm assuming the beta Gimp is installed through flatpak.  Not sure what the "gimp-data"is that can be seen with Synaptic Package Manager - what would happen if I remove that?

---

### Post by Dennis N on 2021-01-22
> I'm assuming the beta Gimp is installed through flatpak.  Not sure what the "gimp-data"is that can be seen with Synaptic Package Manager - what would happen if I remove that?
gimp needs gimp-data to work (it called a dependency), so apt won't allow you to remove gimp-data without also removing gimp.

---

### Post by jmichaels29 on 2021-01-22
> **Dennis N said:**
> gimp needs gimp-data to work (it called a dependency), so apt won't allow you to remove gimp-data without also removing gimp.

Thanks for your reply!

It's interesting that it's called "gimp-data/focal,focal,now 2.10.18-1"

The last stable version I had installed was version 2.10.20, and the beta version I have now is version 2.99.4

But the beta version still needs that data - interesting.

---

### Post by deadflowr on 2021-01-22
> **jmichaels29 said:**
> Thanks for your reply!

It's interesting that it's called "gimp-data/focal,focal,now 2.10.18-1"

The last stable version I had installed was version 2.10.20, and the beta version I have now is version 2.99.4

But the beta version still needs that data - interesting.

gimp-data would be leftover from the Ubuntu repository version of gimp that was installed.
Should be removable with
```
sudo apt autoremove
```
if that does **not** remove it you can simply run
```
sudo apt purge gimp-data
```

No flatpak-based package should ever need any apt-based package.
It would more or less break the entire concept of flatpaks.

---

### Post by Paddy Landau on 2021-01-23
@deadflowr is correct. You can remove gimp-data, because the flatpak version comes with its own dependencies, which are independent of the DEB (apt) versions. I have no DEB gimp apps installed. (I've used the snap version rather than the flatpak version, but the concept is the same.)

Once the stable gimp version has been updated without the bug, you can remove the flatpak version (as you can see, you have the flathub-beta installed) and install the stable version.

Remove the beta version:
```
flatpak uninstall org.gimp.GIMP
```
Install the stable version. You can use flatpak or snap, whichever you prefer (Ubuntu prefers snap, but you are free to disagree).
EITHER flatpak:
```
flatpak install flathub org.gimp.GIMP
```
OR snap:
```
snap install gimp
```
Be aware that when you uninstall, you might lose all your configuration options. Flatpak options are stored in this folder (note the dot before "var"):
```
~/.var/app/org.gimp.GIMP/config
```
I don't know if you can simply back up that folder before uninstalling, and restore it after installing the stable version.
**EDIT:** I've just realised that flatpak doesn't delete your configuration files, so you should find that your settings are retained after reinstalling.

---

### Post by jmichaels29 on 2021-01-23
ok, thanks.  I removed it with Synaptic and the beta version still runs fine - thanks!

---

### Post by jmichaels29 on 2021-01-23
Thanks for all that info - will be very useful in the future!

---

### Post by jmichaels29 on 2021-01-23
> **deadflowr said:**
> gimp-data would be leftover from the Ubuntu repository version of gimp that was installed.
Should be removable with
```
sudo apt autoremove
```
if that does remove it you can simply run
```
sudo apt purge gimp-data
```

No flatpak-based package should ever need any apt-based package.
It would more or less break the entire concept of flatpaks.

That sudo apt autoremove is a very useful command - just read about it!

---

