---
title: "headphone jack not working"
date: 2011-06-03
forum: Multimedia Software
---

### Post by silverhaze06 on 2011-06-03
running 64bit ubuntu 11.04 on my new toshiba satellite l-655-s5150

the headphone jack does not work, but the internal speakers work fine. i mostly use my computer for audio production, so ubuntu is pretty useless if i can't hook up a decent pair of headphones to it. and for that reason i'm forced to use windows until then. i really hate using windows so PLEASE HELP!

---

### Post by lidex on 2011-06-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by silverhaze06 on 2011-06-04
it gives me 

```
--2011-06-03 23:47:33--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 77.48.224.243
Connecting to www.alsa-project.org|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2011-06-03 23:47:37--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to www.alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                  ] 27,247      85.4K/s   in 0.3s    

2011-06-03 23:47:41 (85.4 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.
```

---

### Post by lidex on 2011-06-04
> **silverhaze06 said:**
> it gives me 

```
--2011-06-03 23:47:33--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 77.48.224.243
Connecting to www.alsa-project.org|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2011-06-03 23:47:37--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to www.alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                  ] 27,247      85.4K/s   in 0.3s    

2011-06-03 23:47:41 (85.4 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.
```

Run the command again and when it prompts to upload key in Y and hit enter. You will then be provided with the url of your alsa-info. Post that link here.

---

### Post by silverhaze06 on 2011-06-04
[http://www.alsa-project.org/db/?f=a743c9d601d2caf3336e3ea96aa2ec395b3f6fcd](http://www.alsa-project.org/db/?f=a743c9d601d2caf3336e3ea96aa2ec395b3f6fcd)

---

### Post by lidex on 2011-06-04
You have two entries in alsa-base.conf that need to go. Open for editing:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Remove this line:
```
options snd-hda-intel model=eapd probe_mask=1 position_fix=1
```
Edit this line:
```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```
to look like this:
```
options snd-hda-intel model=thinkpad
```
Save. Close. Reboot.

---

### Post by silverhaze06 on 2011-06-04
IT WORKS! thank you very, very much!

---

### Post by lidex on 2011-06-04
You're welcome! Please mark the thread solved using 'Thread Tools' up top.

---

### Post by fubar990 on 2011-07-02
G'day lidex

I wonder if you could coach me through mine the same way.  Have a Asus A6000 laptop here with no headphone jack audio,  Here's the link you were asking for:

[http://www.alsa-project.org/db/?f=0d66c77c8d5816ad730b3e583f9dabaa07c8e9f9](http://www.alsa-project.org/db/?f=0d66c77c8d5816ad730b3e583f9dabaa07c8e9f9)

Cheers
Fubar

---

### Post by lidex on 2011-07-02
> **fubar990 said:**
> G'day lidex

I wonder if you could coach me through mine the same way.  Have a Asus A6000 laptop here with no headphone jack audio,  Here's the link you were asking for:

[http://www.alsa-project.org/db/?f=0d66c77c8d5816ad730b3e583f9dabaa07c8e9f9](http://www.alsa-project.org/db/?f=0d66c77c8d5816ad730b3e583f9dabaa07c8e9f9)

Cheers
Fubar

You don't have a mixer element for headphone, but you do have one for line playback currently muted and turned down as well. First try that control.
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

Also look in 'sound preferences' ,on the output tab, and toggle the 'connector' option.

No joy? Try this using a Terminal.
```
echo "options snd-hda-intel model=asus" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by mira3573 on 2011-07-06
I have an HP Mini 311.  Below is the alsa information script url:

[http://www.alsa-project.org/db/?f=d82d65f5eb1f7c493a396455f5d17ac45bf766ef](http://www.alsa-project.org/db/?f=d82d65f5eb1f7c493a396455f5d17ac45bf766ef)

And yes, my headphones do not work but internal speakers do.

thanks!

---

### Post by rafaszola on 2011-07-30
Hi,

I wonder if you could help me. In my case neither the Jack or the internal MIC are working. I generated that URL as you said for the others and it looks a little different than the others as my output does not have the "Jack" description as the others. My URL is

[http://www.alsa-project.org/db/?f=35721be0b06efb7c719b9022ac296ec3d05b7332](http://www.alsa-project.org/db/?f=35721be0b06efb7c719b9022ac296ec3d05b7332)

and I am using a LENOVO G470.

---

### Post by mike255 on 2011-08-01
Hi, 
Can I have some help with this too?

[http://www.alsa-project.org/db/?f=e97b98227f99a65fe9a795dda8a35f9b97284393](http://www.alsa-project.org/db/?f=e97b98227f99a65fe9a795dda8a35f9b97284393)

Internal speakers work well, but once the headphone jack is inserted, the sound disappears at all.
The laptop is Asus G60VX

---

### Post by markkuehler on 2011-08-03
Thanks very much for the info! These steps worked for my Toshiba T135D running Natty!

---

### Post by lidex on 2011-08-17
@mira3573
If you're still out there. Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=hp-m4" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

@rafaszola
I'm not sure what to do here. I see you've instituted the fix for the mic, but apparently that doesn't help with headphones. Try removing that line from alsa-base.conf and replacing with one of these models:
```
 
  laptop        Basic Laptop config (default)
  hp-laptop     HP laptops, e g G60
  asus          Asus K52JU, Lenovo G560
  dell-laptop   Dell laptops
  dell-vostro   Dell Vostro
  olpc-xo-1_5   OLPC XO 1.5
  ideapad       Lenovo IdeaPad U150
  thinkpad      Lenovo Thinkpad

```

One at a time please until something works. Ideapad and thinkpad are where I would start. 
Syntax: options snd-hda-intel model=xxxx

@mike255
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=asus-mode3" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by snarkyshakes on 2011-08-17
Internal speaker working, headphone jack not.
[http://www.alsa-project.org/db/?f=d8c3beb1de2f0ca19df3f75a272968cd2ba3bbfe](http://www.alsa-project.org/db/?f=d8c3beb1de2f0ca19df3f75a272968cd2ba3bbfe)

Ideas? Much thanks in advance.....

---

### Post by lidex on 2011-08-18
> **snarkyshakes said:**
> Internal speaker working, headphone jack not.
[http://www.alsa-project.org/db/?f=d8c3beb1de2f0ca19df3f75a272968cd2ba3bbfe](http://www.alsa-project.org/db/?f=d8c3beb1de2f0ca19df3f75a272968cd2ba3bbfe)

Ideas? Much thanks in advance.....

Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by snarkyshakes on 2011-08-20
Worked mint. Thanks!

---

### Post by rbonazzo on 2011-08-22
Hi,
I have a sony vaio and yes headphone don't work

[http://www.alsa-project.org/db/?f=5e94fc24892b02a1bbaa039b9cf866f1aa4af9b4](http://www.alsa-project.org/db/?f=5e94fc24892b02a1bbaa039b9cf866f1aa4af9b4)


Pls help me

Thx

Rinaldo

Pls can some body help me? 
Thx
Rinaldo

---

### Post by finomeno on 2011-08-24
Hello!

I am having the same problem with my Lenovo G470. Well, sort of...

*mode=laptop* solves my mic not working, but messes up the headphones jack (when I plug my cans in they stay silent and the sound continues to play through the internal speakers).

*mode=ideapad* does the reverse - fixes the headphones jack, but messes up the mic (it disappears from alsamixer and pavucontrol has no effect on it).

Any help would be much appreciated.

Here's the link to my ALSA information: [http://www.alsa-project.org/db/?f=7dcf62c9806baf44f5cb40a9ace29a01285e5459]("http://www.alsa-project.org/db/?f=7dcf62c9806baf44f5cb40a9ace29a01285e5459")

Thank you!

---

### Post by kortez on 2011-08-24
@lidex
 If you are still helping, it would be much appreciated. The sound works fine with the internal speakers but the headphone jack does nothing.
Link to the info: [http://www.alsa-project.org/db/?f=9dd2bd4dcd196628b91367b738a8627840dd037b](http://www.alsa-project.org/db/?f=9dd2bd4dcd196628b91367b738a8627840dd037b)

---

### Post by gquipster on 2011-08-25
Hi,

Hate to jump onto the band wagon - but I have a Dell Vostro laptop that I cannot get the headphone jack working on either.

My alsa information can be found here: [http://www.alsa-project.org/db/?f=116f2574f29995d48ad0a6005bb4db71088648c4](http://www.alsa-project.org/db/?f=116f2574f29995d48ad0a6005bb4db71088648c4)

Appreciate any help as I'd like to be able to listen to music whilst working. 

G

---

### Post by lidex on 2011-08-25
> **kortez said:**
> @lidex
 If you are still helping, it would be much appreciated. The sound works fine with the internal speakers but the headphone jack does nothing.
Link to the info: [http://www.alsa-project.org/db/?f=9dd2bd4dcd196628b91367b738a8627840dd037b](http://www.alsa-project.org/db/?f=9dd2bd4dcd196628b91367b738a8627840dd037b)


Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=thinkpad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by capnkarama on 2011-08-26
I am having the same problem with my headphone jack not working.

The link to my information is:


[http://www.alsa-project.org/db/?f=dd6f124233fb684b8f5ff227183bfbffe0791ec8](http://www.alsa-project.org/db/?f=dd6f124233fb684b8f5ff227183bfbffe0791ec8)

Any help is greatly appreciated!

---

### Post by kortez on 2011-08-28
> Quote:
Originally Posted by kortez View Post
@lidex
If you are still helping, it would be much appreciated. The sound works fine with the internal speakers but the headphone jack does nothing.
Link to the info: [http://www.alsa-project.org/db/?f=9d...a8627840dd037b](http://www.alsa-project.org/db/?f=9d...a8627840dd037b)

Try this using a Terminal="Applications->Accessories->Terminal"
Code:

echo "options snd-hda-intel model=thinkpad" | sudo tee -a /etc/modprobe.d/alsa-base.conf

Reboot
 I tried this and still no working headphone jack. I know it is not broken because it works in windows. Any ideas?

---

### Post by lidex on 2011-08-28
> **kortez said:**
> I tried this and still no working headphone jack. I know it is not broken because it works in windows. Any ideas?

Make sure to check your settings in alsamixer and sound preferences.Then try changing the model from thinkpad to ideapad.
For editing:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

---

### Post by lidex on 2011-08-28
> **capnkarama said:**
> I am having the same problem with my headphone jack not working.

The link to my information is:


[http://www.alsa-project.org/db/?f=dd6f124233fb684b8f5ff227183bfbffe0791ec8](http://www.alsa-project.org/db/?f=dd6f124233fb684b8f5ff227183bfbffe0791ec8)

Any help is greatly appreciated!

You have two model settings in alsa-base.conf.
Remove one and change the model on the other to thinkpad.
No help? Try ideapad.

---

### Post by finomeno on 2011-08-29
Hello lidex,

Could you have a look at my situation too, please.

I am having the same problem with my Lenovo G470.
I have tried different settings, but none of them work completely:

*mode=laptop* solves my mic not working, but messes up the headphones jack (when I plug my cans in they stay silent and the sound continues to play through the internal speakers).

*mode=ideapad* does the reverse - fixes the headphones jack, but messes up the mic (it disappears from alsamixer except for volume and boost, and pavucontrol has no effect on it either).

All the latest updates installed, including the latest BIOS flash from Lenovo.

Any help would be much appreciated.

Here's the link to my ALSA information: [http://www.alsa-project.org/db/?f=f2e0f878a0aee2d4c7761b77bedc57a5c7d87a52]("http://www.alsa-project.org/db/?f=f2e0f878a0aee2d4c7761b77bedc57a5c7d87a52")

Thank you!

---

### Post by lidex on 2011-08-29
> **finomeno said:**
> Hello lidex,

Could you have a look at my situation too, please.

I am having the same problem with my Lenovo G470.
I have tried different settings, but none of them work completely:

*mode=laptop* solves my mic not working, but messes up the headphones jack (when I plug my cans in they stay silent and the sound continues to play through the internal speakers).

*mode=ideapad* does the reverse - fixes the headphones jack, but messes up the mic (it disappears from alsamixer except for volume and boost, and pavucontrol has no effect on it either).

All the latest updates installed, including the latest BIOS flash from Lenovo.

Any help would be much appreciated.

Here's the link to my ALSA information: [http://www.alsa-project.org/db/?f=f2e0f878a0aee2d4c7761b77bedc57a5c7d87a52]("http://www.alsa-project.org/db/?f=f2e0f878a0aee2d4c7761b77bedc57a5c7d87a52")

Thank you!

These are the model options:
```
 
  laptop        Basic Laptop config (default)
  hp-laptop     HP laptops, e g G60
  asus          Asus K52JU, Lenovo G560
  dell-laptop   Dell laptops
  dell-vostro   Dell Vostro
  olpc-xo-1_5   OLPC XO 1.5
  ideapad       Lenovo IdeaPad U150
  thinkpad      Lenovo Thinkpad

```
You should try them all if you haven't already. You see the asus model is even specified for lenovo g560 and that may have the same configuration as yours. Alsa is automagically selecting the ideapad model for you:
```
[   15.785652] ALSA hda_codec.c:3986 hda_codec: model 'ideapad' is selected for config 17aa:0 (Lenovo)
```
So you need to counteract it.

[COLOR="Magenta"]EDIT: Here you go:
[http://ubuntuforums.org/showpost.php?p=11022416&postcount=230](http://ubuntuforums.org/showpost.php?p=11022416&postcount=230)[/COLOR]

---

### Post by rbonazzo on 2011-08-30
Hello lidex,

Could you have a look at my situation too, please.

Here's the link to my ALSA information: [http://www.alsa-project.org/db/?f=5e...f866f1aa4af9b4](http://www.alsa-project.org/db/?f=5e...f866f1aa4af9b4)
Thank you!

Rinaldo

---

### Post by lidex on 2011-08-30
> **rbonazzo said:**
> Hello lidex,

Could you have a look at my situation too, please.

Here's the link to my ALSA information: [http://www.alsa-project.org/db/?f=5e...f866f1aa4af9b4](http://www.alsa-project.org/db/?f=5e...f866f1aa4af9b4)
Thank you!

Rinaldo

Check your link. I'm getting nothing.

---

### Post by rbonazzo on 2011-08-31
Hi lidex sorry for the error, the correct url is 
[http://www.alsa-project.org/db/?f=c71509e6711eb34f6400f1c32e96a5e16ed3bf29](http://www.alsa-project.org/db/?f=c71509e6711eb34f6400f1c32e96a5e16ed3bf29)

Thank you

---

### Post by lidex on 2011-08-31
> **rbonazzo said:**
> Hi lidex sorry for the error, the correct url is 
[http://www.alsa-project.org/db/?f=c71509e6711eb34f6400f1c32e96a5e16ed3bf29](http://www.alsa-project.org/db/?f=c71509e6711eb34f6400f1c32e96a5e16ed3bf29)

Thank you

Your model name in alsa-base.conf is laptop - add these parameters to it:
```
position_fix=1 enable=yes
```
so it looks like this:
```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```
To edit:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Save. Close. Reboot.

---

### Post by rbonazzo on 2011-09-01
> **lidex said:**
> Your model name in alsa-base.conf is laptop - add these parameters to it:
```
position_fix=1 enable=yes
```
so it looks like this:
```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```
To edit:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Save. Close. Reboot.

Hi lidex, made the change but still not working.
:( 
Rinaldo

---

### Post by gquipster on 2011-09-02
Hi Lidex,

Would really appreciate your help.

Have tried everything I can think of - including manually upgrading and rebuilding ALSA - but still can't get any sound through the headphones.

Plugging headphones in cuts out the speakers - but no sound comes out.

This is my ALSA info: [http://www.alsa-project.org/db/?f=8630fbc475346d10c7ab8463f4c77bebba88e00b](http://www.alsa-project.org/db/?f=8630fbc475346d10c7ab8463f4c77bebba88e00b)

Many thanks in advance

---

### Post by lidex on 2011-09-02
> **gquipster said:**
> Hi Lidex,

Would really appreciate your help.

Have tried everything I can think of - including manually upgrading and rebuilding ALSA - but still can't get any sound through the headphones.

Plugging headphones in cuts out the speakers - but no sound comes out.

This is my ALSA info: [http://www.alsa-project.org/db/?f=8630fbc475346d10c7ab8463f4c77bebba88e00b](http://www.alsa-project.org/db/?f=8630fbc475346d10c7ab8463f4c77bebba88e00b)

Many thanks in advance

Do me a favor and remove the model name entry from alsa-base.conf, reboot, and run the info script again. Thanks.

---

### Post by lidex on 2011-09-02
> **rbonazzo said:**
> Hi lidex, made the change but still not working.
:( 
Rinaldo

Leave everything the same and follow the link in my sig to upgrade alsa.

---

### Post by gquipster on 2011-09-05
> **lidex said:**
> Do me a favor and remove the model name entry from alsa-base.conf, reboot, and run the info script again. Thanks.

Hi,

Sorry for delay - was on holiday.

[http://www.alsa-project.org/db/?f=b3a89ab803d6cca9f19852279d8282fbfcde50ff](http://www.alsa-project.org/db/?f=b3a89ab803d6cca9f19852279d8282fbfcde50ff)

Thanks

G

---

### Post by finomeno on 2011-09-08
Thank you lidex,

> **lidex said:**
> These are the model options:
```
 
  laptop        Basic Laptop config (default)
  hp-laptop     HP laptops, e g G60
  asus          Asus K52JU, Lenovo G560
  dell-laptop   Dell laptops
  dell-vostro   Dell Vostro
  olpc-xo-1_5   OLPC XO 1.5
  ideapad       Lenovo IdeaPad U150
  thinkpad      Lenovo Thinkpad

```


None of them did the trick. Still the same issue: *ideapad* works for headphones and *laptop* works for the mic.

> 
```
[   15.785652] ALSA hda_codec.c:3986 hda_codec: model 'ideapad' is selected for config 17aa:0 (Lenovo)
```
So you need to counteract it.


I probably need some extra options to go along with the *ideapad* setting to make the mic work again.

> 
[COLOR="Magenta"]EDIT: Here you go:
[http://ubuntuforums.org/showpost.php?p=11022416&postcount=230](http://ubuntuforums.org/showpost.php?p=11022416&postcount=230)[/COLOR]


This was another post of mine. Didn't solve the issue though.

Any new info would be much appreciated!
Thank you!

---

### Post by rbonazzo on 2011-09-09
> **lidex said:**
> Leave everything the same and follow the link in my sig to upgrade alsa.
Hi Lidex thx for your reply.

Try your suggest now the headphone work but I can not disable the PC speaker

So when when I use skype disturbing my colleagues who can hear my conversations

:confused:

Regards Rinaldo

---

### Post by wgarciamachmar on 2011-09-13
I have the same problem!! Help please.

[http://www.alsa-project.org/db/?f=c471932c98e205f071b92ea30726cbd44ddec215](http://www.alsa-project.org/db/?f=c471932c98e205f071b92ea30726cbd44ddec215)

---

### Post by lidex on 2011-09-14
> **rbonazzo said:**
> Hi Lidex thx for your reply.

Try your suggest now the headphone work but I can not disable the PC speaker

So when when I use skype disturbing my colleagues who can hear my conversations

:confused:

Regards Rinaldo

Post an updated alsa-info please.

---

### Post by rbonazzo on 2011-09-14
Hi Lidex here' my updated alsa-info [http://www.alsa-project.org/db/?f=ccde0eb43af8bc627bef103a7aceba39889e1b9a](http://www.alsa-project.org/db/?f=ccde0eb43af8bc627bef103a7aceba39889e1b9a)
Thx again
Rinaldo

---

### Post by vietduc on 2011-09-15
@lidex: I have same problem, help me please[COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C][/COLOR][/FONT][/COLOR]
my link: [http://www.alsa-project.org/db/?f=bb27c165605a1616e1d33834afcb314acdb3dd88](http://www.alsa-project.org/db/?f=bb27c165605a1616e1d33834afcb314acdb3dd88)

thank again

---

### Post by eteh003 on 2011-09-16
Hi lidex! I am encountering the same problem. Laptop built-in speakers works but as soon as i plug my headphones no sound is produced. Could you please have a look at mine as well? 
alsa-info: [http://www.alsa-project.org/db/?f=4d442e148e9cc4bf4c3e407ea960df0b5f8cb9bb](http://www.alsa-project.org/db/?f=4d442e148e9cc4bf4c3e407ea960df0b5f8cb9bb)
Thanks a lot!!

---

### Post by gquipster on 2011-09-17
Hi Lidex,

Any chance to look at this yet?

G

> **gquipster said:**
> Hi,

Sorry for delay - was on holiday.

[http://www.alsa-project.org/db/?f=b3a89ab803d6cca9f19852279d8282fbfcde50ff](http://www.alsa-project.org/db/?f=b3a89ab803d6cca9f19852279d8282fbfcde50ff)

Thanks

G

---

### Post by Koala Kid on 2011-09-17
Hello lidex,

I have a simple Logitech headset + mic, once once the plug is jacked in, it doesn't switch the sound to the headset.
On pavucontrol, when I choose manually to stream on HDMI conroller, there's no sound.

here's my alsa-info script output:
[http://www.alsa-project.org/db/?f=2e...a35d786fca6ffb](http://www.alsa-project.org/db/?f=2e...a35d786fca6ffb)

here's aplay -L output while streaming on HDMI:
```

default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
surround40:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=Live,DEV=0
    SB Live! Value [CT4670], Multichannel Capture/PT Playback
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    Direct sample mixing device
dmix:CARD=Live,DEV=2
    SB Live! Value [CT4670], Multichannel Capture/PT Playback
    Direct sample mixing device
dmix:CARD=Live,DEV=3
    SB Live! Value [CT4670], Multichannel Playback
    Direct sample mixing device
dsnoop:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    Direct sample snooping device
dsnoop:CARD=Live,DEV=2
    SB Live! Value [CT4670], Multichannel Capture/PT Playback
    Direct sample snooping device
dsnoop:CARD=Live,DEV=3
    SB Live! Value [CT4670], Multichannel Playback
    Direct sample snooping device
hw:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    Direct hardware device without any conversions
hw:CARD=Live,DEV=2
    SB Live! Value [CT4670], Multichannel Capture/PT Playback
    Direct hardware device without any conversions
hw:CARD=Live,DEV=3
    SB Live! Value [CT4670], Multichannel Playback
    Direct hardware device without any conversions
plughw:CARD=Live,DEV=0
    SB Live! Value [CT4670], ADC Capture/Standard PCM Playback
    Hardware device with all software conversions
plughw:CARD=Live,DEV=2
    SB Live! Value [CT4670], Multichannel Capture/PT Playback
    Hardware device with all software conversions
plughw:CARD=Live,DEV=3
    SB Live! Value [CT4670], Multichannel Playback
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
```



your help would be appreciated.

---

### Post by DevadasMallya on 2011-09-17
I'm facing the same problem.. When I plug in my headphones I'm not able to hear anything but external speakers are working fine. The result from running the wget command is located at [http://www.alsa-project.org/db/?f=123df76264662f97f983ad53f3997aa3d438f740](http://www.alsa-project.org/db/?f=123df76264662f97f983ad53f3997aa3d438f740)

---

### Post by lidex on 2011-09-27
> **DevadasMallya said:**
> I'm facing the same problem.. When I plug in my headphones I'm not able to hear anything but external speakers are working fine. The result from running the wget command is located at [http://www.alsa-project.org/db/?f=123df76264662f97f983ad53f3997aa3d438f740](http://www.alsa-project.org/db/?f=123df76264662f97f983ad53f3997aa3d438f740)

Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by finomeno on 2011-10-02
Update for **Lenovo G470** (and possibly for some other Lenovo *Essential* and *Ideapad* series laptops/notebooks).

After several updates (from official ubuntu repos, not PPAs) one of the modes did the trick for me (albeit with a little glitch).

Making sure you have the latest alsa drivers installed and inserting ```
options snd-hda-intel model=asus
``` into */etc/modprobe.d/alsa-base.conf* enables the internal mic and the switching between speakers/headphones.

**Note** that you might need to ajust sound/mic volumes through PulseAudio Volume Control (pavucontrol) and check for the correct devices through PulseAudio Device Chooser (padevchooser). For more details on this see [u0x's blog]("http://u0x.blog138.fc2.com/?no=98").

The only downside for me at this time is that the mic volume is quite low and there is static noise, although not enough to make a Skype conversation unintelligible or uncomfortable.

Hope this helps those looking to fix sound issues on their Lenovos.
Any tips on getting rid of the mic static altogether greatly appreciated.

---

### Post by Tigerbone on 2011-10-11
Toshiba L655-5158  >> when i plug in my headphones the sound keeps playing from the internal speakers...can you plz have a look and help me thank u much

[http://www.alsa-project.org/db/?f=750e4b0091885bdecdaffd3bf426a0fe7991ad8c](http://www.alsa-project.org/db/?f=750e4b0091885bdecdaffd3bf426a0fe7991ad8c)

---

### Post by SylentO on 2011-10-11
Not sure if you are still lending your assistance, but your help would be greatly appreciated! My problem is that the Sound works fine until headphones are plugged in, then speaker sound is muted, but no sound from headphones. All returns to normal when headphones are removed.

Gateway M-7356U Laptop, Mobile Intel GL40 Express Chipset,I ntel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) using Conexant CX20561 (Hermosa) Codec on Ubuntu 11.04, I am using the latest ALSA update.

ALSA info at:
[http://www.alsa-project.org/db/?f=4b29369688e80eb754f09fce4586524806600a1e](http://www.alsa-project.org/db/?f=4b29369688e80eb754f09fce4586524806600a1e)

I have tried modifying the alsabase.conf via: gksu gedit /etc/modprobe.d/alsa-base.conf
and have tried these following settings individually to no avail:
options snd-hda-intel model=auto
options snd-hda-intel model=laptop
options snd-hda-intel model=hp-laptop
options snd-hda-intel model=asus
options snd-hda-intel model=dell-laptop
options snd-hda-intel model=dell-vostro
options snd-hda-intel model=olpc-xo-1_5
options snd-hda-intel model=ideapad
options snd-hda-intel model=thinkpad
 
I've also submitted a bug at: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/870080](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/870080)

---

### Post by rafaszola on 2011-10-13
Thanks Finomeno! I've been struggling with this problem for a while. Now it is fixed. Amazing.

---

### Post by Dingelfranz on 2011-10-13
Hey guys...
I've just updated from 10.04 to 11.10, and now my "line out" option in the mixer is gone :(
So headphones only work while internal speakers are playing aswell... Can I get it back in any way?
Any help would be greatly appreciated!

[http://www.alsa-project.org/db/?f=9f48d2148878e278262f9381abf99ea5044c245e](http://www.alsa-project.org/db/?f=9f48d2148878e278262f9381abf99ea5044c245e)

---

### Post by www.rzr.online.fr on 2011-11-01
Related :

[http://ubuntuforums.org/showthread.php?p=11416524#post11416524](http://ubuntuforums.org/showthread.php?p=11416524#post11416524)

[http://rzr.online.fr/q/hda](http://rzr.online.fr/q/hda)

---

### Post by vmosorio on 2011-11-01
Hello all!

I have been looking for an appropriate place to post this question without luck, hope not to bug you with this but I have no choice.

I use a machine with Ubuntu 10.04 to record audio with Ardour, I can record and playback fine but there is a little problem I'm having with the line input:  I have an external mixer where the mics and everything else is hooked up to then the main output of this mixer goes to the soundcard input, and of course the audio output of the soundcard comes back to one of the mixer channels so I can playback the audio from the PC. 
The problem is that when I record from mics I need to mute the line in playthrough so I don't get feedback ... BUT the audio properties only shows a tab with "input" which I can mute unmute and adjust level.  Actually I could leave the playthrough permanently off since I monitor all the inputs in the mixer board rather than in the PC speakers... any idea?  thank you very much to all!


Since nobody seems to know about this issue, I ended up changing the SB live soundcard and leaving the built in soundcard of the PC's motherboard, it seems that the line playthrough is disabled in this one so I don't get that loud feedback I get with the SB card. It is very strange though that all OS's are deleting the line in control in playback and leaving just the line in for record mode control available, I hear the same complain from Vista users.  If someone can suggest Ubuntu about this, please explain that line in playthrough and line in capture are two different things :)

---

### Post by rbonazzo on 2011-11-02
Hi, after trying the suggestion I still have the same problem, please help me thx

[http://www.alsa-project.org/db/?f=3d443e95b228abf09531b503eda07f928f05be2b](http://www.alsa-project.org/db/?f=3d443e95b228abf09531b503eda07f928f05be2b)

Rinaldo

---

### Post by R3Porter_FX on 2011-11-02
Any help would be greatly appreciated!

[www.alsa-project.org/db/?f=dc24db0317626b09043aa187a7d439103ff54074](www.alsa-project.org/db/?f=dc24db0317626b09043aa187a7d439103ff54074)

Special  TnX

---

### Post by mikene on 2011-12-04
Same issue in [here]("http://www.alsa-project.org/db/?f=7476838698e22cefbb04be7d73b45af88913626d") :frown:

Any help would be appreciated !

---

### Post by lidex on 2011-12-27
> **rbonazzo said:**
> Hi, after trying the suggestion I still have the same problem, please help me thx

[http://www.alsa-project.org/db/?f=3d443e95b228abf09531b503eda07f928f05be2b](http://www.alsa-project.org/db/?f=3d443e95b228abf09531b503eda07f928f05be2b)

Rinaldo

Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=thinkpad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by rbonazzo on 2011-12-28
> **lidex said:**
> Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=thinkpad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

Thx now it's work

Rinaldo

---

### Post by Marcelo Fernández on 2011-12-28
> **finomeno said:**
> Update for **Lenovo G470** (and possibly for some other Lenovo *Essential* and *Ideapad* series laptops/notebooks).

After several updates (from official ubuntu repos, not PPAs) one of the modes did the trick for me (albeit with a little glitch).

Making sure you have the latest alsa drivers installed and inserting ```
options snd-hda-intel model=asus
``` into */etc/modprobe.d/alsa-base.conf* enables the internal mic and the switching between speakers/headphones.

**Note** that you might need to ajust sound/mic volumes through PulseAudio Volume Control (pavucontrol) and check for the correct devices through PulseAudio Device Chooser (padevchooser). For more details on this see [u0x's blog]("http://u0x.blog138.fc2.com/?no=98").

The only downside for me at this time is that the mic volume is quite low and there is static noise, although not enough to make a Skype conversation unintelligible or uncomfortable.

Hope this helps those looking to fix sound issues on their Lenovos.
Any tips on getting rid of the mic static altogether greatly appreciated.

Great Finomeno, I've had the same problem with a Lenovo Ideapad G470 in Ubuntu 11.10. The internal mic were not working, but plugging an external one did.

I added "options snd-hda-intel model=asus" to the /etc/modprobe.d/alsa-base file and rebooting. Now both microphones work.

Thank you!
Marcelo

---

### Post by neu5eeCh on 2011-12-28
Holy earbuds, Batman! Looks like some of these are being solved! I would love to get my mic jack working on my HP Pavilion dv1000 laptop. If I run Audacity, and press record, I can't get audacity to record my voice, but if I unplug the mic from the mic jack, audacity seems to record the "click" of the mic jack being removed? It acts as though there's a volume setting somewhere that needs to be cranked? I've tried alsamixer, in terminal, but nothing seems to help. Please hold my hand. Please!

**P.S.** Everything works as it should except for the mic. External speakers and speaker jacks work just fine. Neither the internal nor external (mic jack) works.


[http://www.alsa-project.org/db/?f=2cf3c58dc13721097fb329924475e36d79e7b287](http://www.alsa-project.org/db/?f=2cf3c58dc13721097fb329924475e36d79e7b287)

---

### Post by MoreOrLess on 2011-12-29
VTPoet: I would try using this in /etc/modprobe.d/alsa-base.conf
```
options snd-hda-intel model=laptop-eapd
```

---

### Post by Tralce on 2012-01-01
Hey lidex!

You seem to be helping a lot of people here, so I hope you can help me with the same issue that everyone seems to be having. 

I've installed Oneiric on an Asus G50Vt (Best Buy edition, I suppose) and of course the headphone jack does not work at all in Linux. 

I've tried adding lines to alsa-base.conf to no avail, which is sad because I fixed this on my own with my last g50v on 9.10 with this little script that rebuilt alsa from source. 

Anyway, here's my alsa-info.sh output.

[http://www.alsa-project.org/db/?f=8c7d5157ee92e83820abf695347af19bc50ac705](http://www.alsa-project.org/db/?f=8c7d5157ee92e83820abf695347af19bc50ac705)

---

### Post by MoreOrLess on 2012-01-01
> **Tralce said:**
> Hey lidex!

You seem to be helping a lot of people here, so I hope you can help me with the same issue that everyone seems to be having. 

I've installed Oneiric on an Asus G50Vt (Best Buy edition, I suppose) and of course the headphone jack does not work at all in Linux. 

I've tried adding lines to alsa-base.conf to no avail, which is sad because I fixed this on my own with my last g50v on 9.10 with this little script that rebuilt alsa from source. 

Anyway, here's my alsa-info.sh output.

[http://www.alsa-project.org/db/?f=8c7d5157ee92e83820abf695347af19bc50ac705](http://www.alsa-project.org/db/?f=8c7d5157ee92e83820abf695347af19bc50ac705)
[http://www.linlap.com/wiki/asus+g50v](http://www.linlap.com/wiki/asus+g50v)

---

### Post by lidex on 2012-01-02
> **MoreOrLess said:**
> [http://www.linlap.com/wiki/asus+g50v](http://www.linlap.com/wiki/asus+g50v)

That should work.

---

### Post by Mr Nemo on 2012-01-13
Hey lidex, you've helped so many people, think you could help one more?

Here's the info from the script

```
http://www.alsa-project.org/db/?f=3291effde00e6420972097a931842754339588e7
```I'm running Ubuntu 11.10 on a Dell XPS 15 L502x

I have two headphone jacks. One labeled S/P DIF and a non labeled one. The labeled one works but I can't control the volume. The non labeled one works if i boot up with the headphones plugged in but stops working if i take them out and try to plug them in again.

---

### Post by MoreOrLess on 2012-01-14
@Mr Nemo: I found this from someone with the same model
> Actually I have a sound issue. When I plug the headphones or Monitoring speakers, I need to go to the System sound preferences and select Analog output instead of Headphones Output. In the middle you have a SPIDF output which is not to use unless with digital devices. This is related to the alsa driver which is not capable of autodetecting the input/output choice. Ironhide or Bumblebee can affect the sound configuration for HDMI sound (NVIDIA audio) but not the native onboard sound card.
Go to Sound Settings under HARDWARE tab and tell me what is in there, you should have several Sound outputs (HDMI ones, Analog and Duplex&#8230;). Make sure the Duplex is the choosen one.

---

### Post by Mr Nemo on 2012-01-14
Thanks for the reply MoreOrLess,

I have analog stereo duplex selected, but I still have the same problem.

---

### Post by ocoee on 2012-01-15
Any chance somebody might be able to help with getting mine to work as well? 


[http://www.alsa-project.org/db/?f=2082d5c03dc5f3846f41bf92d38261e6dfc34751](http://www.alsa-project.org/db/?f=2082d5c03dc5f3846f41bf92d38261e6dfc34751)

---

### Post by shizz on 2012-01-16
Hey I see you've helped a lot of people here i was wondering if you could help me. Speakers work fine but the headphones don't output any sound. I've ran a few of the commands you have suggested to other people but it doesn't seem to have helped me. [http://www.alsa-project.org/db/?f=b09f6f20ce88352c0689ca197853fe9cf38204d4](http://www.alsa-project.org/db/?f=b09f6f20ce88352c0689ca197853fe9cf38204d4)

Thanks in advance.

Also I was wondering, any idea why it seems to be a problem with a lot of people?

---

### Post by MoreOrLess on 2012-01-16
> snd-hda-intel: model=asus-mode3
snd-hda-intel: model=thinkpad
snd-hda-intel: model=asus

One at a time... Remove those lines from /etc/modrprobe.d/alsa-base.conf. They're for other codecs. Here is your codec list (only four keywords):
```
ALC269
======
  basic		Basic preset
  laptop-amic	Laptops with analog-mic input
  laptop-dmic	Laptops with digital-mic input
  auto		auto-config reading BIOS (default)
```

I have a feeling you need to unmute something in alsamixer or play with hda-analyzer.

---

### Post by shizz on 2012-01-16
> **MoreOrLess said:**
> One at a time... Remove those lines from /etc/modrprobe.d/alsa-base.conf. They're for other codecs. Here is your codec list (only four keywords):
```
ALC269
======
  basic		Basic preset
  laptop-amic	Laptops with analog-mic input
  laptop-dmic	Laptops with digital-mic input
  auto		auto-config reading BIOS (default)
```

I have a feeling you need to unmute something in alsamixer or play with hda-analyzer.

I'm told there is no such file or directory?

---

### Post by MoreOrLess on 2012-01-16
What do you mean? If you can't find the file, use a GUI like nautilus..
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

---

### Post by shizz on 2012-01-16
> **MoreOrLess said:**
> What do you mean? If you can't find the file, use a GUI like nautilus..
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

Hmmm that opened it. I straight copied your last command in and put gksudo gedit before it aswell. Oh well it opened now. 

btw do you mean remove a line save and reboot then try the next? or all at once?

---

### Post by MoreOrLess on 2012-01-16
> **shizz said:**
> btw do you mean remove a line save and reboot then try the next?
Yes, but you don't need to reboot:
```
sudo alsa force-reload
```

---

### Post by shizz on 2012-01-16
> **MoreOrLess said:**
> Yes, but you don't need to reboot:
```
sudo alsa force-reload
```

Ok I did what you said and it hasn't helped. 

When I open alsa mixer the headphones output just shows no bar to increase volume in, just a box with 00 written in it.

Also I noticed something in another thread where they said if they change the sound settings from "analogue Headphones" to "analogue Speakers" when the headphones are plugged in then the headphones work, this happens to me.

Also I've always been able to hear a faint sound coming through the headphones but it isn't changeable.

Dunno if this extra info helps or not. 

Thanks for your help.

---

### Post by pratikemc2 on 2012-01-20
Hi,

I to have the same problem please help me,I am using ThinkPad R61

my url is
[http://www.alsa-project.org/db/?f=82eddf2dbc7252ac89d7ac402f748154cefdbe84](http://www.alsa-project.org/db/?f=82eddf2dbc7252ac89d7ac402f748154cefdbe84)

---

### Post by MoreOrLess on 2012-01-21
@pratikemc2: Based on this ( [http://www.insanelymac.com/forum/index.php?showtopic=142307](http://www.insanelymac.com/forum/index.php?showtopic=142307) ), I'm guessing you need to use a program called hdaanalyzer (google it) to enable the headphones.

---

### Post by SlimboKarvell on 2012-03-06
Hello,

Could someone help me with the same problem please? I have an Asus Eee PC, Ubuntu 10.04 and my headphone with mic doesn't work. Sound work well and I get a "noise" when I plug the microphone in, but in PulseAudio Control I only get a very small reaction in the "input" when the mic is connected.

Here is the Alsa information: [http://www.alsa-project.org/db/?f=23516dd71f872113e6f9d3fe17595ded7b3694ac](http://www.alsa-project.org/db/?f=23516dd71f872113e6f9d3fe17595ded7b3694ac)

Thank you!

---

### Post by shizz on 2012-03-06
> **SlimboKarvell said:**
> Hello,

Could someone help me with the same problem please? I have an Asus Eee PC, Ubuntu 10.04 and my headphone with mic doesn't work. Sound work well and I get a "noise" when I plug the microphone in, but in PulseAudio Control I only get a very small reaction in the "input" when the mic is connected.

Here is the Alsa information: [http://www.alsa-project.org/db/?f=23516dd71f872113e6f9d3fe17595ded7b3694ac](http://www.alsa-project.org/db/?f=23516dd71f872113e6f9d3fe17595ded7b3694ac)

Thank you!

I still haven't fixed the problem I have with headphones but I found a fix. It might only be a minor fix but this works for me. Go to sound in the settings. Under output, when you have the headphones plugged in, switch the output from headphones to speakers and it should work. 

I'm using 11.10 so I couldn't tell you if it will work with you but give it a try. It's a minor inconvenience.

---

### Post by mrkrik on 2012-05-09
Hi,

My headphone jack is not working despite fiddling with the alsamixer settings and the front end settings (system>sound) I can't get the headphones even to appear in the hardware menu.

I am running the new 12.04

My log is at [http://www.alsa-project.org/db/?f=e677ebb9d465ccc7d9e2361746c81f0a25f2f987](http://www.alsa-project.org/db/?f=e677ebb9d465ccc7d9e2361746c81f0a25f2f987)

any help greatly appreciated as I'm stuck without my music and have just signed up for Spotify!

---

### Post by adroitster on 2012-05-24
I helping my friend to setup ubuntu who is a first time user. It's an ASUS K55VD-DS71 laptop.

Following codecs are being reported on the system when I issue the command cat /proc/asound/card0/codec* | grep Codec

Codec: Realtek ALC270 Codec: Intel PantherPoint HDMI`

Using the ALSA information script v0.4.60 I have obtained information about my alsa setup and device which is [here]("http://www.alsa-project.org/db/?f=d803ad0523fb069e9bdb7ead7dd39d56bccde362")

The interesting thing is that Pulse Audio sound settings reports only one device and that is Headphones (Build in Audio) BUT the sound comes only from speaker even if speakers are not listed there. There is no sound from the headphones.

I played around with alsamixer a bit and also alsa-base.conf a bit and once got the sound working from headphones but after restart the same problem as described above reappeared.

If I could get it to work once I believe there must be something really trivial which I am missing here. Can someone please suggest me what should I do ? Thanks in advance.

P.S : It's her first time on Ubuntu so I am trying to make the transition from windows as smooth as possible. A non-working hardware especially headphones can be a major roadblock.

---

### Post by ddm101 on 2012-05-25
Heeadphones jack not working since I performed an upgrade to 12.04

[http://www.alsa-project.org/db/?f=a8b11775ebf922ac82e6fb98cf2c63c247691cbe](http://www.alsa-project.org/db/?f=a8b11775ebf922ac82e6fb98cf2c63c247691cbe)

---

### Post by Slapyourbaby on 2012-05-25
Internal speakers work. Headphones do not. Here is my info and I appreciate all the help you guys are providing. 

[http://www.alsa-project.org/db/?f=7ac111b2bd0beb8b8d7cfaea952e547f84931793](http://www.alsa-project.org/db/?f=7ac111b2bd0beb8b8d7cfaea952e547f84931793)

EDIT: I should mention I am on 10.04

---

### Post by adroitster on 2012-05-25
> **Slapyourbaby said:**
> Internal speakers work. Headphones do not. Here is my info and I appreciate all the help you guys are providing. 

[http://www.alsa-project.org/db/?f=7ac111b2bd0beb8b8d7cfaea952e547f84931793](http://www.alsa-project.org/db/?f=7ac111b2bd0beb8b8d7cfaea952e547f84931793)

EDIT: I should mention I am on 10.04

Open the file ```
sudo gedit /etc/modprobe.d/alsa-base.conf
``` and add this line at the end of the file ```
options snd-hda-intel model=laptop-amic
```. Then reboot. Check if everything works as expected. If not then remove that line and try adding this and reboot ```
options snd-hda-intel model=laptop-dmic
```

If none of that works then try to upgrade your ALSA drivers from [here]("https://help.ubuntu.com/community/HdaIntelSoundHowto#Update_to_the_Latest_Version_of_ALSA"). If after the upgrade the problem is not solved then try the steps mentioned above again.

---

### Post by ddm101 on 2012-05-29
> **ddm101 said:**
> Headphones jack not working since I performed an upgrade to 12.04

[http://www.alsa-project.org/db/?f=a8b11775ebf922ac82e6fb98cf2c63c247691cbe](http://www.alsa-project.org/db/?f=a8b11775ebf922ac82e6fb98cf2c63c247691cbe)

Sorry for reposting this, but I haven't gotten any help yet.

Anywho, thanks in advance.

---

### Post by Bacilio on 2012-05-30
my sound works good, but very often my headphone jack stops working. i tried a few things, but no luck. then i turn it off and the next day it works again, but only to later go out again. can anyone plz help me?? 

[http://www.alsa-project.org/db/?f=26ecf2f19a255235ac207b8c80a0d75b484b4bd0]("http://www.alsa-project.org/db/?f=26ecf2f19a255235ac207b8c80a0d75b484b4bd0")

---

### Post by adroitster on 2012-05-30
> **ddm101 said:**
> Sorry for reposting this, but I haven't gotten any help yet.

Anywho, thanks in advance.

Open this link [http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt) and search for "**ALC662**" . Find the right model for your laptop.

Then replace ```
laptop_model
``` in the following code ```
options snd-hda-intel model=**laptop_model**
``` with the model of your laptop you just found from the link above and add it to *alsa-base.conf*. Reboot your system.

Try using different models under **ALC662** in alsa-base.conf until you find the one that works for you.

You can edit* alsa-base.conf* using command ```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

---

### Post by adroitster on 2012-05-30
> **Bacilio said:**
> my sound works good, but very often my headphone jack stops working. i tried a few things, but no luck. then i turn it off and the next day it works again, but only to later go out again. can anyone plz help me?? 

[http://www.alsa-project.org/db/?f=26ecf2f19a255235ac207b8c80a0d75b484b4bd0]("http://www.alsa-project.org/db/?f=26ecf2f19a255235ac207b8c80a0d75b484b4bd0")

I think you are probably facing one of the bugs listed here : [http://voices.canonical.com/david.henningsson/](http://voices.canonical.com/david.henningsson/) . 

If you believe you are facing a similar problem as described in that article then try this workaround : [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/946232/comments/32](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/946232/comments/32)

---

### Post by Bacilio on 2012-05-31
**[COLOR="Blue"]i really appreciate the help there.. i'll look into it, but if anything. i will try and save for a new laptop and sell this. thnk you adroitster [/COLOR]**

---

### Post by ddm101 on 2012-06-05
> **ddm101 said:**
> heeadphones jack not working since i performed an upgrade to 12.04

[http://www.alsa-project.org/db/?f=a8b11775ebf922ac82e6fb98cf2c63c247691cbe](http://www.alsa-project.org/db/?f=a8b11775ebf922ac82e6fb98cf2c63c247691cbe)


bump

---

### Post by adroitster on 2012-06-05
> **ddm101 said:**
> bump

Hey! 

Did you try following what I mentioned in my previous reply?

---

### Post by ddm101 on 2012-06-06
> **adroitster said:**
> Hey! 

Did you try following what I mentioned in my previous reply?

Sorry for insisting, but for some reason my bookmarked page never showed any post beyond mine, so i saw your answer just now.

My laptop has sound (although choppy if you turn the volume up to 60% or more) but my PC is the one with the issue. The latter doesn't really have a brand or model since it was built by me some years ago, so I wouldn't know what to replace that line with - Should I just test all of them?

I could supply my hardware info if that would help, but I should add the front headphone jack was working just fine in 11.10.

Anywho, thanks a lot for the help. I'll try your solution and post back to let you know if it worked.

---

### Post by adroitster on 2012-06-06
> **ddm101 said:**
> Sorry for insisting, but for some reason my bookmarked page never showed any post beyond mine, so i saw your answer just now.

My laptop has sound (although choppy if you turn the volume up to 60% or more) but my PC is the one with the issue. The latter doesn't really have a brand or model since it was built by me some years ago, so I wouldn't know what to replace that line with - Should I just test all of them?

I could supply my hardware info if that would help, but I should add the front headphone jack was working just fine in 11.10.

Anywho, thanks a lot for the help. I'll try your solution and post back to let you know if it worked.

If it's a desktop then try using the generic one's listed under ALC662.

---

### Post by ddm101 on 2012-06-06
> **adroitster said:**
> If it's a desktop then try using the generic one's listed under ALC662.

Just to be clear, the closest thing I have to this line:

**options snd-hda-intel model=laptop_model**

Is this line:
[B]
options snd-intel8x0m index=-2[/B]

Should I replace the **"-2"** with one of the generic lines?

Thanks for the patience.

---

### Post by adroitster on 2012-06-06
> **ddm101 said:**
> Just to be clear, the closest thing I have to this line:

**options snd-hda-intel model=laptop_model**

Is this line:
[B]
options snd-intel8x0m index=-2[/B]

Should I replace the **"-2"** with one of the generic lines?

Thanks for the patience.

I am sorry I should have been more specific. You have to paste this line : ```
options snd-hda-intel model=laptop_model
``` at the end of that file but replace **laptop_model** with one of the models under ALC662. See if any of those generic models work for you.

---

### Post by ddm101 on 2012-06-06
> **adroitster said:**
> I am sorry I should have been more specific. You have to paste this line : ```
options snd-hda-intel model=laptop_model
``` at the end of that file but replace **laptop_model** with one of the models under ALC662. See if any of those generic models work for you.

Tried all the generic ones with no luck. Thanks a lot for the help anyway Adroidster.

---

### Post by WillFS on 2012-06-20
@lidex

I am having the same problem on my 64bit toshiba satellite L645 S4102. Audio works great but headphones wont output sound and the speakers stay on.

ALSA info link: [http://www.alsa-project.org/db/?f=39224a3a6ef8926fd3f51d9eb9d13d6add6672c3](http://www.alsa-project.org/db/?f=39224a3a6ef8926fd3f51d9eb9d13d6add6672c3)

Please help me solve this problem. Thanks!

Will

---

### Post by Sorky on 2012-08-03
> Looks like I have the same problem...

Rear output works but front headphone output does not (although connecting tothe front headphone output is "seen" as the the rear output stops)!

64bit 12.04 Server 

Gigabyte H77M-D3H motherboard with Intel i7 3770 

Tried adding the line to the .conf file

Link: [http://www.alsa-project.org/db/?f=87c34569f5a436cffe929ecf255ef106d28b4a2f](http://www.alsa-project.org/db/?f=87c34569f5a436cffe929ecf255ef106d28b4a2f)

Solved/Workaround - Not sure if there is a better or more correct way, but this worked... In alsamixer I found "Independ" which was ON - pressed up/down to make it OFF and got sound out of the from headphones ;-)
[]("http://www.alsa-project.org/db/?f=87c34569f5a436cffe929ecf255ef106d28b4a2f")

---

### Post by herakler on 2012-11-04
plzz helpe me , this is my link

[http://www.alsa-project.org/db/?f=fe505f3a29cf4f16e5d58a1b207e61f3a014ff9d](http://www.alsa-project.org/db/?f=fe505f3a29cf4f16e5d58a1b207e61f3a014ff9d)

---

### Post by Bacilio on 2012-11-15
i been having problems too since i updated from 11.04 to 12.10.... headphone jack just doesnt respond... somedays i get lucky and it works... but that hasnt happened in a while now. i made a switch to windows, and the headphone jack works perfect.. but dont want windows... back to 12.10 and no luck... can anyone help me out please... much appreciated. 

[http://www.alsa-project.org/db/?f=e3c4b621ca064992ebb3684ace69a031b72b1338]("http://www.alsa-project.org/db/?f=e3c4b621ca064992ebb3684ace69a031b72b1338")

---

### Post by xdeathcorex on 2012-11-16
Hi, I have the same issue with the rest. I'm using Asus K55VD. Weird part is both the speaker and earphone jack cannot produce any sound. Please help. Here's my details:

[http://www.alsa-project.org/db/?f=1f5140c144704ed54ba38e6882835eac721fb120](http://www.alsa-project.org/db/?f=1f5140c144704ed54ba38e6882835eac721fb120)

Thank you.

---

### Post by toxictruth on 2012-11-24
Same issue Asus K55A

Alsa code : [http://www.alsa-project.org/db/?f=0abd9d491bc0fbdf3bf705b1156aa163fc269d34](http://www.alsa-project.org/db/?f=0abd9d491bc0fbdf3bf705b1156aa163fc269d34)

Please Advise!

---

### Post by cayzar on 2013-05-04
I have the same issue. I know this is an old thread but I am hoping someone can help!!!! Thanks in advance.

 [http://www.alsa-project.org/db/?f=4cc401fdc1e924471c6a30eb2054fa2547e128dc](http://www.alsa-project.org/db/?f=4cc401fdc1e924471c6a30eb2054fa2547e128dc)

HP DV6 laptop

---

### Post by dhruboroy29 on 2013-05-08
Dear All,

I'm using a Dell Precision WorkStation T3400  running Ubuntu 12.10. The past few hours I've been unsuccessfully trying to get my Skullcandy headphones to work. My ALSA information script URL is:

[http://www.alsa-project.org/db/?f=fb34f924b1afb6b7a12fdb8ea1c7d76df21ad1e9](http://www.alsa-project.org/db/?f=fb34f924b1afb6b7a12fdb8ea1c7d76df21ad1e9)

If someone could point out the right settings for me, that would be great!

Thanks and Regards,
Dhrubo.

---

### Post by indrajithgihan on 2013-05-21
Hi, 
I have ASUS K55VD and my head phone connected speakers not working. But inbuilt speakers works fine. I have upgraded to Ubuntu 13.04 64-bit.
This is what you want - [http://www.alsa-project.org/db/?f=8714140087768a286e490c0d08040b646988a1e8](http://www.alsa-project.org/db/?f=8714140087768a286e490c0d08040b646988a1e8)

Please assist

---

