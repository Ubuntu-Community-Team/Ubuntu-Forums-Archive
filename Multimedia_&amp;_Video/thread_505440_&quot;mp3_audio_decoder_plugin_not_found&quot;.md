---
title: "&quot;mp3 audio decoder plugin not found&quot;"
date: 2007-07-20
forum: Multimedia &amp; Video
---

### Post by dascheer on 2007-07-20
when i open k3b i get this error message:
"Mp3 Audio Decoder plugin not found.  K3b could not load or find the Mp3 decoder plugin. This means that you will not be able to create Audio CDs from Mp3 files. Many Linux distributions do not include Mp3 support for legal reasons.  Solution: To enable Mp3 support, please install the MAD Mp3 decoding library as well as the K3b MAD Mp3 decoder plugin (the latter may already be installed but not functional due to the missing libmad). Some distributions allow installation of Mp3 support via an online update tool (i.e. SuSE's YOU)."

I have tried every single codec, decoder in the package libraries and nothing's changed.  my dvd/cd burner works great.  im a n00b, so please go easy on me.

---

### Post by dougfractal on 2007-07-20
> I have tried every single codec, decoder in the package libraries and nothing's change


does that mean you have ```
sudo apt-get install libmad0 lame
sudo aptitude install libk3b2-mp3

```

visit [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_MP3_support_for_K3b](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_MP3_support_for_K3b)

good luck with ubuntu

---

### Post by burnman99 on 2007-07-20
Make sure you have libmad0 installed and libk3b-mp3 that should do it.

Later

Rog

---

### Post by dascheer on 2007-07-21
i installed libk3b-mp3 and it worked! yeahhhhhhhh!

---

### Post by bwfs2003 on 2007-07-21
I am having the same problem with rhythbox music player. I have installed as suggested above, but it still doesn't want to work.

Any ideas ??:confused:

---

### Post by dougfractal on 2007-07-22
Use > system >Administration>software_sources   = enable all of ubuntu's source list.


```
sudo apt-get install gstreamer0.10-fluendo-mp3

```

also while you are there, for others


```
sudo apt-get install totem-gstreamer gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-gl gstreamer0.10-ffmpeg

```

---

### Post by Jored on 2007-07-23
I have Xubuntu 7.04 and following your inatructions I got Movie Player to play .wmv videoclips and .mp3 music successfully. However, I cannot get gxine to play any mp3 files.

On another note, I am unable to listen live to any of my bookmarks radio stations, which worked fine with Media Player, Real Player and Adobe Flashplayer on Windows. Obviously Media Player is out of the question, but I installed flashplayer and still cannot listen to internet radio. And I've downloaded Real Player from their website but, as a newbie, do not know how to install. The download consists of many programs I don't know what to do with. Synaptic does not find it.

---

### Post by RomeReactor on 2007-07-23
Hi. For Gxine, you need to install the following packages:
```
sudo apt-get install libxine1 libxine1-ffmpeg libxine-extracodecs
```

To install Real Player, get it form [here]("http://www.real.com/linux"); the downloaded file will be named **RealPlayer10GOLD.bin**. Once it finishes downloading, move it to your home folder, open a terminal (Applications->Accessories->Terminal) and enter:
```
sudo chmod +x RealPlayer10GOLD.bin
```
to make the file executable, and then:
```
sudo ./RealPlayer10GOLD.bin
```

---

### Post by Jored on 2007-07-23
Thank you. I've installed Real Player as you advised and got a message that it has installed successfully, yet I can't find it anywhere (??).  Neither with Appfinder, Synaptic nor the Add/Remove application.
:confused:

---

### Post by RomeReactor on 2007-07-23
It won't show up in Add/Remove or Synaptic because you didn't install it from a .deb file. Did it make an entry in "Applications->Sound & Video->Real Player 10"?

---

### Post by Jored on 2007-07-23
No, no entry there. When I was going through the installation process a question about directory came up (can't remember exactly the wording) and I answered Y (I knew no better). It came back saying that Real Player was now configured correctly (??) and eventually that installation had completed successfully. I then exitted the terminal.

By the way, your gxine tip worked fine. Thank you.

---

### Post by RomeReactor on 2007-07-23
If it installed in the default directory, it should have made a menu entry. Try restarting the panels (sometimes newly installed applications don't show up right away in the menus, and it's useful to restart the panels): open the System Monitor (System->Administration->System Monitor), on the **Processes** tab right-click on **gnome-panel** and select "Kill Process" (nothing to worry about, this only restarts the panel, though it's not recommended you kill other applications unless they're misbehaving). Once the panels restart, go to "Applications->Sound & VIdeo" and see if RealPlayer shows up now.

If it still doesn't, you'll have to make an entry for Real Player: right-click on the top menubar and select **Edit Menus**. Highlight **Sound & Video** on the left pane, and on the right one press "New Item", and fill it out like this:

* Type: Application
* Name: RealPlayer 10
* Command: realplay
* Comment: RealNetworks' open source media player

The icon should be located here: **/usr/share/icons/hicolor/48x48/apps/realplay.png**.

---

### Post by Jored on 2007-07-24
I have Xubuntu with Xfce. There is no >Administration->System Monitor entry in System. 

I then tried the Edit Menu route but there is no Sound & Video entry, just Settings. I clicked on the Edit tab, then Add Menu Entry but there is no Application option, just Title, Menu, Launcher, Separator and Quit choices.

---

### Post by RomeReactor on 2007-07-24
Sorry, I though you were using Gnome; in the case of XFCE:

* Title: RealPlayer 10
* Menu: (I imagine this is where you choose where you want RealPlayer to show up)
* Launcher: realplay
* Separator: (don't know about this, sorry)
* Quit: To finish editing the launcher, I suppose.

The advice of someone who actually uses XFCE will be more useful to you with this issue.

---

### Post by gregb49 on 2007-09-22
Thanks for the KIIIB and Real Player tips - worked fine with KUBUNTU 7.04 for me. Greg

PS. For Real Player I chose for directory ```
/etc/realplayer
```and then when asked the next question, that meant nothing to me, I entered their suggestion of ```
/usr
``` An entry appeared in MULTIMEDIA and works fine with an MP3 file. This on a new install of KUBUNTU 7.04

---

