---
title: "giPlayer working again"
date: 2014-06-19
forum: Multimedia Software
---

### Post by mr bob on 2014-06-19
Hello,

For people who would like to use giPlayer (a GUI wrapper for get_iplayer - to download BBC tv and radio programmes in the UK), I've got it working for Ubuntu 14.04.

This distro doesn't seem to pre-install dependencies, so you have to install get-iplayer and libav-tools manually, if they are not already installed.


1) Open terminal (Control+Alt+T) 
2) Install dependencies (if not already installed) 
```
    
    sudo apt-get install get-iplayer 
    sudo apt-get install libav-tools 

```
3) Download giPlayer.deb [http://sourceforge.net/projects/giplayer/]("http://sourceforge.net/projects/giplayer/")
4) Install giPlayer from terminal:
```

    cd Downloads 
    sudo dpkg -i giPlayer.deb 

```


cheers :)

---

### Post by ajgreeny on 2014-06-19
Whilst I am sure this will be great for many users of get-iplayer, for my purpose it is not a great deal of help as there is no possible way, unless I have just missed it, to search for programme titles, or categories, nor get all the information about a programme as you can with the command line version.

I have made several aliases for some of the commands I commonly use,which simplifies the rather difficult to remember syntax of the cli, and makes it just about as good as giPlayer, though of course you may disagree and still prefer a GUI.
```
alias gip='get_iplayer'
alias gipc='get_iplayer --category'
alias gipg='get_iplayer -g'
alias gipghd='get_iplayer --vmode=flashhd --get'
alias gipi='get_iplayer --info'
alias gipr='get_iplayer --type radio'

```All I have to add to these aliases is the programme number which I get from either the gip or gipr alias command.

---

### Post by mr bob on 2014-06-19
Yes giPlayer is a very straightforward simple GUI for get_iplayer. There are many features such as info that get_iplayer can do that giPlayer can't.

However, you can search for a programme in giPlayer. Put in the title or part of the title of the programme and click either the TV or Radio button. This will give you a list of programmes.

---

### Post by ajgreeny on 2014-06-19
Thanks for that.
I didn't notice that the box was a search-box.

Can you search for title only; not for category, such as music, or news, or comedy, etc etc?

---

### Post by mr bob on 2014-06-19
No just the programme title I'm afraid.

---

### Post by mr bob on 2015-02-24
Hello UK users,

The giPlayer project on SourceForge had been closed for a few months because the BBC changed its search feeds, which stopped get_iplayer from working, which giPlayer requires.

However, there is a version of get_iplayer that is working again with a 7-day search and you can now download with the BBC iPlayer URL or programme id.
You need to add a PPA for get_iplayer and install version 2.87 or higher:
instructions for get_iplayer are here: [https://github.com/get-iplayer/get_iplayer/wiki/ubuntu](https://github.com/get-iplayer/get_iplayer/wiki/ubuntu)

So, Ubuntu forum user Lantizia had updated giPlayer and encouraged me to restart the giPlayer project and I have done so:
It now has an updated UI so that a programme can be downloaded from the BBC iPlayer PID or URL.
I have also written browser extensions for Firefox and Chromium. When on a BBC iPlayer or radio page, a button can be clicked that executes giPlayer with the PID.

You can get the deb installer and browser extensions here: [http://sourceforge.net/projects/giplayer/files/]("http://sourceforge.net/projects/giplayer/files/")

---

### Post by Deakin111 on 2015-06-26
Thanks [COLOR=#000000]Lantizia for your work. I have installed giPlayer on Ubuntu 15.04 as instructed and also added the giPlayer extension in Chromium. It shows in the address bar when a film is being run but does not invoke giPlayer when clicked.

What am I doing wrong.

regards,
John[/COLOR]

---

### Post by mr bob on 2015-06-26
Hi John,

I've tried a fresh install on Ubuntu 14.10 with MATE desktop and had no problems. 

Can you run giPlayer without using the Chromium extension? If you are using the standard Ubuntu desktop (Unity) I can't remember how you open applications but look for giPlayer in Sound & Video or Multimedia?
Otherwise open a terminal and type:
```
python /usr/bin/giplayer.py
```

If nothing happens, then giPlayer hasn't installed properly. Download the deb file from sourceforge and retry to install.

If giPlayer is installed, check the version number. Open the About dialog, in the giPlayer menu: Help->About. It should be version 0.51. If it is an earlier version, try installing 0.51 (instructions as above).

Once you are sure you have the latest version installed correctly, try clicking on the Chromium extension button.

Let me know how you get on.

cheers Mr Bob

---

### Post by Deakin111 on 2015-06-26
Mr Bob,

Sorry I should have mentioned all this stuff. I have giPlayer 0.51 and Chromium 43.etc. giPlayer works fine if I copy and paste the PID and, as I say, the icon appears whenever there is a BBC programme ready to play, the icon just does not respond when I click it. It is not a big deal and I can live with it, its just that it worked fine with Firefox.

regard,
John

---

### Post by Deakin111 on 2015-06-26
Mr Bob,

Sorry I should have mentioned all this stuff. I have giPlayer 0.51 and Chromium 43.etc. giPlayer works fine if I copy and paste the PID and, as I say, the icon appears whenever there is a BBC programme ready to play, the icon just does not respond when I click it. It is not a big deal and I can live with it, its just that it worked fine with Firefox.

regard,
John

---

### Post by mr bob on 2015-06-26
John,

Hi, thanks for the extra information. I tested it with Chromium 43 and it works on my machine. The firefox add-on works totally differently to the Chromium one.

The only thing I can think of, is something is perhaps different if you have the Unity desktop (the standard Ubuntu desktop) but I'd be surprised.

Sorry I can't help, I'm flummoxed. 

regards Mr Bob

---

### Post by Deakin111 on 2015-06-27
Mr Bob,

Thanks for trying. As I say it is no big deal.

John

---

### Post by chome4 on 2015-08-02
I'm getting

croydon@croydon:~$ cd Downloads
croydon@croydon:~/Downloads$ sudo dpkg -i giPlayer.deb
[sudo] password for croydon: 
dpkg: regarding giPlayer.deb containing giplayer, pre-dependency problem:
 giplayer pre-depends on python-gtk2
  python-gtk2 is not installed.

dpkg: error processing archive giPlayer.deb (--install):
 pre-dependency problem - not installing giplayer
Errors were encountered while processing:
 giPlayer.deb
croydon@croydon:~/Downloads$ 

How do I install 'python-gtk2'?

---

### Post by pingadam on 2016-01-24
Thanks Mr Bob for all your work on giPlayer - it has proved to be an excellent GUI for get_iplayer, making it much easier to download BBC programmes.

There's one "fly in the ointment" though regarding the browser extension for Firefox: since Firefox version 43, add-ons need to be signed - see here: [https://support.mozilla.org/en-US/kb/add-on-signing-in-firefox]("https://support.mozilla.org/en-US/kb/add-on-signing-in-firefox")

So - the Firefox giPlayer browser extension will no longer work. *However*, you can override this, as explained in above linked article, by going to **about:config** and toggling the **xpinstall.signatures.required** setting to **false**.

Unfortunately, once Firefox version 46 is released, this will no longer be possible, and all Firefox add-ons / extensions will need to be signed - see the following link:
[https://blog.mozilla.org/addons/2016/01/22/add-on-signing-update/]("https://blog.mozilla.org/addons/2016/01/22/add-on-signing-update/").

So, it may be worth looking into getting the giPlayer Firefox extension signed by Mozilla at some point, before it stops working (see: [https://developer.mozilla.org/en-US/Add-ons/Distribution]("https://developer.mozilla.org/en-US/Add-ons/Distribution")).

Kind regards,

Adam.

---

