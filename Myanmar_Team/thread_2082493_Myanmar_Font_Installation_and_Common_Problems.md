---
title: "Myanmar Font Installation and Common Problems"
date: 2012-11-09
forum: Myanmar Team
---

### Post by mgngapyin on 2012-11-09
I will edit this post little by little, and make it as one-stop guide for common font issues in Myanmar. I hope we don't need to answer the same question again and again on FB groups, blogs, Myanmar forums, etc. 
 
[SIZE=3]I. How many kinds of Myanmmar fonts are there? [/SIZE]
 
Four as far as I know
1. Unicode
2. [COLOR=blue]Ayar [/COLOR]- Unicode[COLOR=blue],[/COLOR] but encoding is slightly modified
3. [FONT=Courier New][COLOR=blue]Zawgyi -[/COLOR][/FONT] Non-Unicode
4. ASCII - Winn Innwa
 
[SIZE=3]II. How to installl Unicode fonts?[/SIZE]
 
If you're using Ubuntu 12.10 (Quantal), you don't need to install Unicode fonts. It's already included in Ubuntu. You can find it in the package [FONT=Courier New][SIZE=2][COLOR=blue]Fonts-sil-padauk[/COLOR][/SIZE][/FONT][FONT=Courier New][SIZE=2].[/SIZE][/FONT]
 
If you're using Ubuntu 12.04 (Precise) or later versions, you can still install [FONT=Courier New][COLOR=blue]Fonts-sil-padauk[/COLOR][/FONT] from the Ubuntu Software center, Terminal or Synaptic Package Manager. 
 
**Other Unicode Fonts ??? **
You can find other unicode fonts in 
 
```
http://www.myanmarlanguage.org/unicode/myanmar-fonts-which-follow-unicode-rules
```**Ethnic Unicode Fonts**
Tharlon supports some ethnic languages
There are other unicode fonts too. I'll add later.
 
[SIZE=3]III. How to install Zawgyi and other Truetype fonts (.ttf)?[/SIZE]
 
Download Zawgyi 2008 from google code
 
```
http://code.google.com/p/zawgyi-keyboard/downloads/detail?name=ZawgyiOne2008.ttf
```Double-click to open it. It'll open the [FONT=Courier New][COLOR=blue]Font Viewer[/COLOR][/FONT]. 
Click [FONT=Courier New][COLOR=blue]Install[/COLOR][/FONT]. 
 
 
**### Should I install Zawgyi 2009?**
 
No. Zawgyi 2009 is incomplete font. Though you can install it in Ubuntu, font may be displayed differently. Windows 8 even detects it as a corrupted font. And most people use Zawgyi 2008. 
 
 
**### What happended if I click [FONT=Courier New][COLOR=blue]In[/COLOR][/FONT][FONT=Courier New][COLOR=blue]stall[/COLOR][/FONT] in [COLOR=blue]Font Viewer[/COLOR]?**
 
In 12.10 (Quantal), the font is installed tp[COLOR=blue] ~/.local/share/fonts [/COLOR]directory. 
 
In 12.04 (Precise), the font is installed to [COLOR=blue]~/.fonts [/COLOR]directory.
 
 
**### Where is ~/.local/share/fonts?**
 
Dot files/folders ( . ) are hidden in the HOME folder. 
Open Home folder. Click [COLOR=blue]Menu » View [/COLOR][COLOR=blue]» Show Hidden Files[/COLOR]. 
Open [COLOR=blue].local [/COLOR][COLOR=blue]» share [/COLOR][COLOR=blue]» fonts[/COLOR] 
There, you'll see ZawgyiOne2008.ttf
 
In Precise (12.04), 
Open [COLOR=blue]HOME[/COLOR] folder
Open [COLOR=blue].fonts[/COLOR] folder
There, you'll see ZawgyiOne2008.ttf
 
[SIZE=3]IV. How to install multiple fonts?[/SIZE]
 
Copy and paste the fonts to ~/.local/share/fonts OR .fonts directory. 
If you can't find the folders, you'll need to create it yourself. 
 
How to create a new folder ?
Right click >> Create New Folder
 
[SIZE=3]V. Problems, Problems that everyone thinks[/SIZE]
 
Though there is Unicode font preinstalled and most of the unicode fonts are supported in many Ubuntu Applications, many people still want to use Zawgyi for personal reasons. 
 
[SIZE=2]**Common Problems in Quantal (12.10)**[/SIZE]
 
Though I installed Zawgyi, fonts are incorrectly displayed in Title bar[SIZE=2] of Firefox.[/SIZE]
 
[SIZE=2][SIZE=2][IMG]http://i.imgur.com/ECmY4.png[/IMG][/SIZE]
 
 
 
 
[SIZE=2][SIZE=2]Or [SIZE=2]ev[SIZE=2]en worse, [SIZE=2]Facebook[SIZE=2] friends[SIZE=2]' names, page[SIZE=2] names or group names appear like this. [/SIZE]
 
[SIZE=2][SIZE=2][IMG]http://i.imgur.com/7QuCb.png[/IMG][/SIZE]
 
[SIZE=2][SIZE=2]**So, **[SIZE=2]**w**[SIZE=2]**hat's wrong here? **[/SIZE]
 
[SIZE=2][SIZE=2]Nothing. [/SIZE]
 
[SIZE=2][SIZE=2]It's not the Ubuntu problem[SIZE=2]. It's the configuration problem. [/SIZE]
 
[SIZE=2][SIZE=2]**Let's start with**[SIZE=2]** the Facebook**[SIZE=2]** problem first. **[/SIZE]
 
[SIZE=2][SIZE=2]Ubuntu 12.10 has Unicode (Padauk font) preinstalled. [/SIZE]
[SIZE=2][SIZE=2]When you inst[SIZE=2]all[SIZE=2] Zawgyi, Zawgyi overides the Padauk font because it [SIZE=2]has more encoding po[SIZE=2]ints. [/SIZE]
 
[SIZE=2][SIZE=2]But ...., Zawgyi is inc[SIZE=2]omplete. [SIZE=2][SIZE=2][SIZE=2][SIZE=2]
 
[SIZE=2][SIZE=2][SIZE=2]If you analyse it more, you'll see that the place where Zawgyi doesn't appear are using Bold fonts. [/SIZE]
 
[SIZE=2][SIZE=2]Padauk is replacing the[SIZE=2]se places[SIZE=2] instead of Zawgyi[SIZE=2]. [/SIZE]
[SIZE=2][SIZE=2]Why[SIZE=2]? [SIZE=2]Simple, because it is better. [/SIZE]
 
[SIZE=2]**[SIZE=2]OK. How to solve it?[/SIZE]**
[/SIZE][/SIZE][/SIZE][/SIZE]
Remove Padauk ??? --- A very bad idea. Why remo[SIZE=2]ve when it[SIZE=2] becomes default?[/SIZE]
 
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]The solution -- Change Font Settings in Firefox 
 
In Firefox, click on [COLOR=blue]Menu » Edit » Preferences[/COLOR]
A new window will appear. 
Click [COLOR=blue]Content[/COLOR]
Click [COLOR=blue]Advanced[/COLOR] in Fonts & Color
You'll see[COLOR=blue] Fonts for Western[/COLOR] & a list of settings. 
 
Click [COLOR=blue]Western[/COLOR] in _Fonts for_ 
Choose [COLOR=blue]Other Languages[/COLOR]
You'll see ( Proportional, Serif, San-serif, MonoSpace & their fonts)
[COLOR=blue]Change the Serif font to Zawgyi One. [/COLOR]
Click [COLOR=blue]OK[/COLOR].
Close the Firefox Preference Windows. 
 
Now, you can see Facebook Names in Zawgyi properly. 
 
**Problems in Chrome and Chromium ?? **
 
In Chrome/Chromium, Zawgyi replaces Padauk completely, so you don't need to change anything if you did like most people did.
If something is not right, 
 
Type [COLOR=blue]chrome://chrome/settings/fonts[/COLOR] in the URL bar
Change the Sans-serif font to Zawgyi-One or the font you used. 
 
Title Bar Fonts .... To be continued[SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][COLOR=blue][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2]
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/COLOR][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

### Post by mgngapyin on 2012-11-09
[SIZE=3]How to Change Title Bar Fonts[/SIZE]
[B]
This post is written in Zawgyi. If you can't view Myanmar text, read the above post.[/B]

Firefox &#4121;&#4157;&#4140; font &#4155;&#4117;&#4100;&#4153;&#4126;&#4156;&#4140;&#4152;&#4155;&#4117;&#4142;&#4152;&#4123;&#4100;&#4153; &#4129;&#4097;&#4143; Windows Title Bar &#4096; font &#4096;&#4141;&#4143; &#4155;&#4117;&#4100;&#4153;&#4117;&#4139;&#4121;&#4122;&#4153;&#4171; 
Title Bar Font &#4096;&#4141;&#4143; &#4155;&#4117;&#4100;&#4153;&#4118;&#4141;&#4143;&#4245;&#4129;&#4112;&#4156;&#4096;&#4153; [COLOR=Blue]Gnome Tweak Tool[/COLOR] or [COLOR=Blue]Ubuntu Tweak[/COLOR] &#4145;&#4102;&#4140;&#4151;&#4125;&#4146;&#4124;&#4141;&#4143;&#4117;&#4139;&#4112;&#4122;&#4153;&#4171;

**How to Install & Use Gnome Tweak Tool **
1. Internet &#4097;&#4154;&#4141;&#4112;&#4153;&#4113;&#4140;&#4152;&#4118;&#4141;&#4143;&#4245;&#4124;&#4141;&#4143;&#4117;&#4139;&#4121;&#4122;&#4153;
2. &#4120;&#4122;&#4153;&#4120;&#4096;&#4153;&#4129;&#4145;&#4117;&#4186;&#4116;&#4140;&#4152;&#4096; [COLOR=Blue]Ubuntu Icon (Dash)[/COLOR] &#4145;&#4124;&#4152;&#4096;&#4141;&#4143; &#4239;&#4157;&#4141;&#4117;&#4153;&#4155;&#4117;&#4142;&#4152; Dash &#4096;&#4141;&#4143; &#4118;&#4156;&#4100;&#4153;&#4151;&#4124;&#4141;&#4143;&#4096;&#4153;&#4117;&#4139;&#4171; 
3. [COLOR=Blue]Software Center[/COLOR] &#4124;&#4141;&#4143;&#4245;&#4123;&#4141;&#4143;&#4096;&#4153;&#4113;&#4146;&#4151;&#4117;&#4139;&#4171; &#4145;&#4117;&#4186;&#4124;&#4140;&#4112;&#4146;&#4151; Ubuntu Software Center &#4096;&#4141;&#4143; &#4239;&#4157;&#4141;&#4117;&#4153;&#4117;&#4139;&#4171;
4. Software Center Search Box &#4121;&#4157;&#4140; [COLOR=Blue]gnome tweak tool [/COLOR]&#4124;&#4141;&#4143;&#4245; &#4123;&#4141;&#4143;&#4096;&#4153;&#4123;&#4157;&#4140;&#4117;&#4139;&#4171;
5. [COLOR=Blue]Tweak Tool[/COLOR] &#4102;&#4141;&#4143;&#4155;&#4117;&#4142;&#4152; &#4145;&#4117;&#4186;&#4124;&#4140;&#4117;&#4139;&#4121;&#4122;&#4153;&#4171; Select &#4124;&#4143;&#4117;&#4153;&#4155;&#4117;&#4142;&#4152; [COLOR=Blue]Install[/COLOR] &#4096;&#4141;&#4143; &#4239;&#4157;&#4141;&#4117;&#4153;&#4117;&#4139;&#4171; 
6. Password &#4145;&#4112;&#4140;&#4100;&#4153;&#4152;&#4123;&#4100;&#4153; &#4123;&#4141;&#4143;&#4096;&#4153;&#4113;&#4146;&#4151;&#4117;&#4139;&#4171; &#4097;&#4111;&#4145;&#4101;&#4140;&#4100;&#4153;&#4151;&#4117;&#4139;&#4171; 
7. Install &#4124;&#4143;&#4117;&#4153;&#4155;&#4117;&#4142;&#4152;&#4126;&#4156;&#4140;&#4152;&#4123;&#4100;&#4153; &#4129;&#4101;&#4141;&#4121;&#4153;&#4152;&#4145;&#4123;&#4140;&#4100;&#4153; &#4155;&#4121;&#4157;&#4140;&#4152;&#4145;&#4124;&#4152;&#4145;&#4117;&#4186;&#4124;&#4140;&#4117;&#4139;&#4121;&#4122;&#4153;&#4171; &#4120;&#4122;&#4153;&#4120;&#4096;&#4153; Launcher &#4121;&#4157;&#4140; Icon &#4112;&#4101;&#4153;&#4097;&#4143;&#4112;&#4141;&#4143;&#4152;&#4124;&#4140;&#4117;&#4139;&#4121;&#4122;&#4153;&#4171; Icon     &#4096;&#4141;&#4143; click &#4124;&#4143;&#4117;&#4153;&#4117;&#4139;&#4171;
8. Fonts &#4096;&#4141;&#4143; &#4145;&#4123;&#4156;&#4152;&#4117;&#4139;&#4171; 
9. [COLOR=Blue]Windows Title Font - Ubuntu Bold[/COLOR] &#4096;&#4141;&#4143; &#4239;&#4157;&#4141;&#4117;&#4153;&#4117;&#4139;&#4171; 
10.[COLOR=Blue] Zawgyi-One[/COLOR] &#4096;&#4141;&#4143; &#4145;&#4123;&#4156;&#4152;&#4117;&#4139;&#4171; 
11. &#4112;&#4155;&#4097;&#4140;&#4152; font &#4126;&#4150;&#4143;&#4152;&#4121;&#4122;&#4153;&#4102;&#4141;&#4143; Zawgyi-One &#4129;&#4101;&#4140;&#4152; &#4112;&#4155;&#4097;&#4140;&#4152; font &#4096;&#4141;&#4143; &#4145;&#4123;&#4156;&#4152;&#4145;&#4117;&#4152;&#4117;&#4139;&#4171;

**How to Install & Use Ubuntu Tweak**
1. Download Ubuntu Tweak from [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/).
2. [COLOR=Blue]Terminal[/COLOR] &#4096;&#4141;&#4143; &#4118;&#4156;&#4100;&#4153;&#4151;&#4117;&#4139;&#4171; (Dash >> Terminal &#4124;&#4141;&#4143;&#4245;&#4123;&#4141;&#4143;&#4096;&#4153;&#4113;&#4146;&#4151;&#4117;&#4139;)
3. ```

sudo apt-get update   
sudo apt-get install gdebi 
``` &#4124;&#4141;&#4143;&#4245;&#4123;&#4141;&#4143;&#4096;&#4153;&#4117;&#4139;&#4171;
4. Open [COLOR=Blue]Downloads[/COLOR] Folder
5. Right click >> Ubuntu Tweak_0.8.2....deb 
6. [COLOR=Blue]Open with GDebi Package Installer[/COLOR] &#4096;&#4141;&#4143; &#4239;&#4157;&#4141;&#4117;&#4153;&#4117;&#4139;&#4171;
7. [COLOR=Blue]Install Package[/COLOR] &#4102;&#4141;&#4143;&#4112;&#4140;&#4096;&#4141;&#4143; &#4239;&#4157;&#4141;&#4117;&#4153;&#4117;&#4139;&#4171; 
8. Password &#4123;&#4141;&#4143;&#4096;&#4153;&#4117;&#4139;&#4171; &#4097;&#4111;&#4145;&#4101;&#4140;&#4100;&#4153;&#4151;&#4117;&#4139;&#4171;
9. After installation, [COLOR=Blue]Dash >> Ubuntu Tweak[/COLOR]
10. [COLOR=Blue]Tweaks [/COLOR]&#4096;&#4141;&#4143; &#4239;&#4157;&#4141;&#4117;&#4153;&#4117;&#4139;&#4171; [COLOR=Blue]Fonts [/COLOR]&#4096;&#4141;&#4143; &#4239;&#4157;&#4141;&#4117;&#4153;&#4117;&#4139;&#4171; 
11. [COLOR=Blue]Windows Title Bar font[/COLOR] &#4121;&#4157;&#4140; [COLOR=Blue]Zawgyi One [/COLOR]&#4096;&#4141;&#4143; &#4145;&#4123;&#4156;&#4152;&#4145;&#4117;&#4152;&#4117;&#4139;&#4171; 
12. &#4112;&#4155;&#4097;&#4140;&#4152; font &#4126;&#4150;&#4143;&#4152;&#4121;&#4122;&#4153;&#4102;&#4141;&#4143; &#4112;&#4155;&#4097;&#4140;&#4152; font &#4096;&#4141;&#4143; &#4145;&#4123;&#4156;&#4152;&#4117;&#4139;&#4171;

---

### Post by mgngapyin on 2012-11-09
[SIZE=3]Ubuntu Myanmar Version & Zawgyi Font Issues[/SIZE]
 
You may not know it, but you can now use Ubuntu in Myanmar starting from 12.10 (Quantal). You can choose Myanmar during the installation or add Burmese in Region & Language later. 
 
Ok. I'm using Ubuntu Myanmar Version. I installed Zawgyi and everything messed up like this. **I can't read anything. Alien Words.**
 
[IMG]http://i.imgur.com/lBWy5.png[/IMG]
 
**Why?**
Because Ubuntu is translated into Myanmar using Unicode. Unicode is internationallly recognised and widely used. (not in Myanmar though :()
 
**Why not Zawgyi?**
Zawgyi is not maintained anymore. License not clear. Internationally not recognized - No one will support it. That's sure. Some issues deep.
 
**OK. My Ubuntu Myanmar Version is messed up now. How to solve it?**
Remove Zawgyi font. 
 
**How? I can't read anything.**
That's not true. If you read it carefully, you still can.
Click on the Folder icon in Launcher. 
Go to Menu 
Click V &#4121;&#4156;&#4100;&#4154;&#4096;&#4157;&#4100;&#4154;&#4152;
Click H &#4125;&#4158;&#4096;&#4154;&#4113;&#4140;&#4152;&#4126;&#4145;&#4140;&#4118;&#4141;&#4143;&#4100;&#4154;&#4121;&#4155;&#4140;&#4152;&#4117;&#4156;&#4117;&#4139; Ctrl+H
Open ~/.local/share/fonts folder
Delete ZawgyiOne2008.ttf
Wait for a few seconds, and everthing will be back to normal.
 
**No, No. I can't go anywhere because I can't read. **
Ok. close everything & go to Desktop.
Press keyboard shortcuts ( Ctrl + Alt + T)
Terminal will open. Copy this code (Ctrl+C)
> rm ~/.local/share/fonts/ZawgyiOne2008.ttfPaste into Terminal (Ctrl+Shift+V)
Wait for a few seconds, and everything will be back to normal. 
 
**OK. I want to use Ubuntu Myanmar Version. How to prevent Zawgyi from changing the font?**
You can change it with the font.conf file. 
First, delete Zawgyi Font and make it as original. 
 
Then create a new empty document in ~/.config/fontconfig/ folder 
Name it as conf.d (note: there is a dot &quot; . &quot; in file name)
If you can't view it, press Ctrl + H to show hidden files. 
Or you can go to menu >> V &#4121;&#4156;&#4100;&#4154;&#4096;&#4157;&#4100;&#4154;&#4152; >> H &#4125;&#4158;&#4096;&#4154;&#4113;&#4140;&#4152;&#4126;&#4145;&#4140;&#4118;&#4141;&#4143;&#4100;&#4154;&#4121;&#4155;&#4140;&#4152;&#4117;&#4156;&#4117;&#4139;
Edit the conf.d like this (just copy and paste)
 
> 
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 
<!-- Use Unicode as default-->
<match target="pattern" name="lang" >
    <test name="lang" qual="any" >
        <string>my</string>
    </test>
    <edit name="family" mode="assign">
        <string>Padauk Book</string>
    </edit>
 
</match>
</fontconfig>
Save it (Ctrl + S) or &#4126;&#4141;&#4121;&#4154;&#4152;&#4102;&#4106;&#4154;&#4152;
 
Open Terminal & type
> fc-cache -f -vto make sure let Ubuntu knows about the change & make sure everything works fine. 
 
type 
> fc-match "my"If you see Padauk Book, it is fine.
 
Now Open Zawgyi One with Font Viewer and install it. 
Wait for some minutes. Nothing changes, right?
It is because we've prevented Zawgyi One from chaning the font. 
 
to confirm it again, Open Terminal & type
> fc-match "my"Padauk-book is still the default. 
 
Padauk Font is too small. You can change the font size in font.conf OR Use Tharlon font, which is bigger. 
 
**How To Make Tharlon as default?**
Open ~/.config/fontconfig/conf.d file & replace [COLOR=blue]Padauk Book[/COLOR] with [COLOR=blue]Tharlon[/COLOR]. 
Save it. Wait for a few seconds. You'll see that it looks bigger. 
 
[IMG]http://i.imgur.com/CqiHR.png[/IMG]
 
**Need to view Facebook, Webpages in Zawgyi?**
Use Firefox Zawgyi to Unicode Converter Add-ons - [https://addons.mozilla.org/en-US/firefox/addon/myanmar-converter/](https://addons.mozilla.org/en-US/firefox/addon/myanmar-converter/)
Use Tagu Extension for Chrome - [https://chrome.google.com/webstore/detail/tagu/ddjpcdpfemhkibhpmgcdbfajdhgpegdk](https://chrome.google.com/webstore/detail/tagu/ddjpcdpfemhkibhpmgcdbfajdhgpegdk)
 
**Need to switch back to Zawgyi temporarily **
Open font.conf and replace with [COLOR=blue]Zawgyi-One[/COLOR]
Save and wait for a few seconds
 
**Need an easier way to switch Unicode (Tharlon) & Zawgyi back and forth **
Use [COLOR=blue]my-fs-cli[/COLOR] from Ubuntu Myanmar Loco Team
 
**Prolems not solved? **
**Zawgyi removed. font.conf not created, but Zawgyi remains**
most likely cause
1. You installed the Zawgyi to System level (not the local folder / Home folder)
2. Where are system level fonts?
/usr/share/fonts/ 
If you installed Zawgyi from Ubuntu-mm launchpad, the fonts are there
> /usr/share/fonts/mm/ZawgyiOne2008.ttf
/usr/share/fonts/mm/Zawgyi-Tai.ttfIf you installed mm-kb.deb keyboard (offline version), the fonts are there
> /usr/share/fonts/mm/ZawgyiOne2008.ttfto remove these, you'll need sudo access or simply use the font.conf
 
**Change the font in font.conf, but nothing changes**
most likely
1. The font you changed is not installed.
2. Try refreshing the font-cache
> fc-cache -f -v3. Still not solved. Log out and log in again.

---

### Post by mgngapyin on 2012-11-11
[SIZE="3"]Chrome/Chromium & Myanmar Font Issues[/SIZE]

I'll be using a lot of pictures. If you've very slow connection, please kindly bear with me. 

In the past, Chromium can't display Myanmar text properly. 

Zawgyi Problems - Words become mixed if they are typed without a word break. 

[IMG]http://i.imgur.com/2j2yJl.png[/IMG]


Unicode Problems - Worse. Can't display at all with most unicode fonts. 

[IMG]http://i.imgur.com/W16rql.png[/IMG]


Padauk can display some text, but still wrong. 

[IMG]http://i.imgur.com/YtzaRl.png[/IMG]



**How to Solve it?**

Until recently there is no solution. 

But "Now", Thanks to the great work by Chromium developers, 

chrome/chromium texts are displaying properly.(see bug here - [https://bugs.webkit.org/show_bug.cgi?id=90362](https://bugs.webkit.org/show_bug.cgi?id=90362) ) Special Thanks to  Kenichi Ishibashi. :KS


You can test the Chrome beta version if you want. 
> [https://www.google.com/landing/chrome/beta/](https://www.google.com/landing/chrome/beta/)

Enter [COLOR="Blue"]chrome://chrome/settings/fonts[/COLOR] in the URL bar
Change the San-Serif font to "Zawgyi" or "Padauk" or "Myanmar3" or "Tharlon" or whatever Myanmar fonts you like. Most of them are working.

In the new version, 

Zawgyi is correctly displayed. No mixing of words anymore. 

[IMG]http://i.imgur.com/l28v2l.png[/IMG]


Unicode is displayed properly too. 

Padauk

[IMG]http://i.imgur.com/84IBql.png[/IMG]

Myanmar 3

[IMG]http://i.imgur.com/Xc5O6l.png[/IMG]


By the way, in myanmar3 font, " U " is wrong, right? 
It is because it is incorrectly typed. " U " has its own unicode point. Someone typed 3 unicode points by mistake ...  Oo + Lone Kyi Tin San Kat + : ... Though they looks like the same, they're not.

That's why I wish everyone use Unicode. Better search index, sorting, spell-check, ....

Unfortunately, there are very few Chromium developers for Ubuntu. So If you want to test Chromium new version, you'll need to build it yourself or just use Chrome Beta. 

If you're a developer, please help in Chromium Ubuntu development.

---

### Post by gipsyhnh on 2012-11-23
Nice Jobs

---

### Post by mgngapyin on 2012-12-08
I have found that changing fontconfig with the "lang" pattern results in ugly English text with some unicode fonts, so I'm trying to correct this with a new fontconfig file. 

> 
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
    <alias>
        <family>sans-serif</family>
        <prefer>
            <family>Droid Sans</family>
            <family>Padauk</family>
        </prefer>
    </alias>
</fontconfig>
What it does is chaning the sans-serif font with fonts in <prefer> tags. Droid Sans will be used first. If there is no Myanmar characters in Droid Sans, it will use Padauk. The English text looks better this way. Since most of the GUI fonts are sans-serif, it should be fine this way.

The drawback is you need to change font settings for browsers. 

For Firefox, type > about:config in the address bar, search for > font.name.sans-serif.x-unicode and change the  string to **Zawgyi-One** to use Zawgyi and **default** for unicode. 

For Chrome/Chrome, go to > chrome://settings/fonts & set the **Sans-serif font** to Zawgyi or Unicode.

---

### Post by yjsu on 2012-12-20
why can't I see myanmar font in terminal well,I can see myanmar font in gedit like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=228944&stc=1&d=1356060444[/IMG]
but it display in terminal like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=228945&stc=1&d=1356060444[/IMG]
why and how to solve it?

---

### Post by Nwe Nwe on 2012-12-21
[QUOTE=mgngapyin;12345828]I will edit this post little by little, and make it as one-stop guide for common font issues in Myanmar. I hope we don't need to answer the same question again and again on FB groups, blogs, Myanmar forums, etc. 
 
[SIZE=3]I. How many kinds of Myanmmar fonts are there? [/SIZE]
 
Four as far as I know
1. Unicode
2. [COLOR=blue]Ayar [/COLOR]- Unicode[COLOR=blue],[/COLOR] but encoding is slightly modified
3. [FONT=Courier New][COLOR=blue]Zawgyi -[/COLOR][/FONT] Non-Unicode
4. ASCII - Winn Innwa
 
[SIZE=3]II. How to installl Unicode fonts?[/SIZE]
 
If you're using Ubuntu 12.10 (Quantal), you don't need to install Unicode fonts. It's already included in Ubuntu. You can find it in the package [FONT=Courier New][SIZE=2][COLOR=blue]Fonts-sil-padauk[/COLOR][/SIZE][/FONT][FONT=Courier New][SIZE=2].[/SIZE][/FONT]
 
If you're using Ubuntu 12.04 (Precise) or later versions, you can still install [FONT=Courier New][COLOR=blue]Fonts-sil-padauk[/COLOR][/FONT] from the Ubuntu Software center, Terminal or Synaptic Package Manager. 
 
**Other Unicode Fonts ??? **
You can find other unicode fonts in 
 
```
http://www.myanmarlanguage.org/unicode/myanmar-fonts-which-follow-unicode-rules
```**Ethnic Unicode Fonts**
Tharlon supports some ethnic languages
There are other unicode fonts too. I'll add later.
 
[SIZE=3]III. How to install Zawgyi and other Truetype fonts (.ttf)?[/SIZE]
 
Download Zawgyi 2008 from google code
 
```
http://code.google.com/p/zawgyi-keyboard/downloads/detail?name=ZawgyiOne2008.ttf
```Double-click to open it. It'll open the [FONT=Courier New][COLOR=blue]Font Viewer[/COLOR][/FONT]. 
Click [FONT=Courier New][COLOR=blue]Install[/COLOR][/FONT]. 
 
 
**### Should I install Zawgyi 2009?**
 
No. Zawgyi 2009 is incomplete font. Though you can install it in Ubuntu, font may be displayed differently. Windows 8 even detects it as a corrupted font. And most people use Zawgyi 2008. 
 
 
**### What happended if I click [FONT=Courier New][COLOR=blue]In[/COLOR][/FONT][FONT=Courier New][COLOR=blue]stall[/COLOR][/FONT] in [COLOR=blue]Font Viewer[/COLOR]?**
 
In 12.10 (Quantal), the font is installed tp[COLOR=blue] ~/.local/share/fonts [/COLOR]directory. 
 
I use Ubuntu 12.10 (Quantal), after installation, i can see Myanmar font but they are not true. So, I install zawgyi.ttf and it has under [COLOR=blue] ~/.local/share/fonts. Now, I can see clearly , but I can't type it, I can't see zawgyi in keybord layout. Can you kindly share how to change keyborad layout. Thanks in advance.[/COLOR]

---

### Post by mgngapyin on 2012-12-21
> **yjsu said:**
> why can't I see myanmar font in terminal well,I can see myanmar font in gedit like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=228944&stc=1&d=1356060444[/IMG]
but it display in terminal like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=228945&stc=1&d=1356060444[/IMG]
why and how to solve it?

Unfortunately, I don't know how to solve this, yjsu. I've tested mlterm, rxvt-unicode terminal emulators, but no success at all. I think Myanmar unicode is not yet supported in Gnome-terminal. Or we might need a better unicode font for console. Since most people refuse to adopt using unicode, everything lags behind. I think you should ask this question at [http://myanmaritpro.com](http://myanmaritpro.com) or [http://mysteryzillion.org](http://mysteryzillion.org) or Myanmar Unicode Facebook page, where the Myanmar unicode initiators visit often.

---

### Post by mgngapyin on 2012-12-21
> **Nwe Nwe said:**
> Now, I can see clearly , but I can't type it, I can't see zawgyi in keybord layout. Can you kindly share how to change keyborad layout. Thanks in advance.

Hi Nwe Nwe,

You can follow the steps mentioned in  [https://www.facebook.com/groups/ubuntu4mm/doc/442170362469082/](https://www.facebook.com/groups/ubuntu4mm/doc/442170362469082/)

Download the mm-kb.deb file
Copy it to Desktop
Open Terminal
type 

> cd Desktop
sudo dpkg -i mm-kb.deb

Open Dash >> Ibus
Click "input methods"
tick "customize active input methods"
select an input method >> burmese >> zawgyi


Shortcut is Ctrl+Space. (You can customize it)
Pressing Left_Shift will also change Zawgyi to English, but **don't use the Left_Shift.** English texts will spread, and a little bit ugly. 

You can view the steps on Youtube. [http://youtu.be/0yttttL7jFo](http://youtu.be/0yttttL7jFo)

---

### Post by mshan on 2012-12-31
ubuntu 12.10 &#4129;&#4112;&#4156;&#4096;&#4153; &#4145;&#4103;&#4140;&#4153;&#4098;&#4154;&#4142; &#4096;&#4142;&#4152;&#4120;&#4143;&#4112;&#4153; &#4240;&#4157;&#4141;&#4117;&#4139;&#4126;&#4124;&#4140;&#4152;&#4170; &#4125;&#4100;&#4153;&#4152;&#4114;&#4143;&#4141;&#4152; &#4121;&#4157;&#4140; &#4126;&#4143;&#4150;&#4152;&#4123;&#4112;&#4146;&#4244; &#4124;&#4096;&#4153;&#4096;&#4156;&#4096;&#4153;&#4117;&#4143;&#4150;&#4101;&#4150;&#4116;&#4146;&#4244; &#4112;&#4144;&#4112;&#4140;&#4096;&#4141;&#4143; &#4124;&#4143;&#4141;&#4097;&#4154;&#4100;&#4153;&#4112;&#4140;&#4117;&#4139;&#4170; system setting --- keyboard layout &#4096;&#4143;&#4141; &#4126;&#4156;&#4140;&#4152;&#4223;&#4117;&#4142;&#4152; Burmese &#4096;&#4142;&#4152;&#4120;&#4143;&#4112;&#4153;&#4096;&#4143;&#4141; &#4145;&#4240;&#4156;&#4152;&#4223;&#4117;&#4142;&#4152; &#4155;&#4121;&#4116;&#4153;&#4121;&#4140;&#4124;&#4143;&#4141; &#4240;&#4143;&#4141;&#4096;&#4153;&#4124;&#4143;&#4141;&#4244; &#4123;&#4112;&#4140; &#4126;&#4141;&#4117;&#4139;&#4112;&#4122;&#4153;&#4170; &#4114;&#4139;&#4145;&#4117;&#4121;&#4146;&#4244; &#4129;&#4146;&#4114;&#4139;&#4096; Zawgyi One font &#4121;&#4127;&#4143;&#4112;&#4153;&#4117;&#4139;&#4120;&#4144;&#4152;&#4170; Libre &#4113;&#4146;&#4121;&#4157;&#4140; &#4101;&#4140;&#4240;&#4143;&#4141;&#4096;&#4153;&#4118;&#4143;&#4141;&#4244; Zawgyi One &#4096;&#4143;&#4141; &#4145;&#4240;&#4156;&#4152;&#4113;&#4140;&#4152;&#4145;&#4117;&#4121;&#4146;&#4244; &#4096;&#4142;&#4152;&#4120;&#4143;&#4112;&#4153; &#4096;&#4143;&#4141; us &#4096;&#4145;&#4116; my &#4096;&#4143;&#4141; &#4145;&#4240;&#4156;&#4152;&#4223;&#4117;&#4142;&#4152; &#4240;&#4143;&#4141;&#4096;&#4153;&#4124;&#4143;&#4141;&#4096;&#4153;&#4112;&#4146;&#4244; &#4129;&#4097;&#4139; &#4145;&#4240;&#4156;&#4152;&#4113;&#4140;&#4152;&#4112;&#4146;&#4244; Zawgyi One font &#4121;&#4127;&#4143;&#4112;&#4153;&#4145;&#4112;&#4140;&#4244;&#4120;&#4146; &#4112;&#4155;&#4097;&#4140;&#4152;&#4127;&#4140; &#4145;&#4155;&#4117;&#4140;&#4100;&#4153;&#4152;&#4126;&#4156;&#4140;&#4152;&#4117;&#4139;&#4112;&#4122;&#4153;&#4170; &#4129;&#4146;&#4126;&#4106;&#4153;&#4124;&#4143;&#4141; &#4121;&#4155;&#4118;&#4101;&#4153;&#4145;&#4129;&#4140;&#4100;&#4153;&#4170; MSWord &#4113;&#4146;&#4121;&#4157;&#4140; &#4145;&#4103;&#4140;&#4153;&#4098;&#4154;&#4142; &#4116;&#4146;&#4244; &#4240;&#4143;&#4141;&#4096;&#4153;&#4123;&#4126;&#4124;&#4143;&#4141; &#4240;&#4143;&#4141;&#4096;&#4153;&#4124;&#4143;&#4141;&#4244;&#4123;&#4121;&#4122;&#4153;&#4244; &#4116;&#4106;&#4153;&#4152;&#4124;&#4121;&#4153;&#4152;&#4121;&#4154;&#4141;&#4147;&#4152; &#4121;&#4240;&#4157;&#4141;&#4120;&#4144;&#4152;&#4124;&#4140;&#4152; &#4097;&#4100;&#4153;&#4119;&#4154;&#4140;...

---

### Post by mgngapyin on 2013-01-01
> **mshan said:**
> ubuntu 12.10 &#4129;&#4112;&#4156;&#4096;&#4153; &#4145;&#4103;&#4140;&#4153;&#4098;&#4154;&#4142; &#4096;&#4142;&#4152;&#4120;&#4143;&#4112;&#4153; &#4240;&#4157;&#4141;&#4117;&#4139;&#4126;&#4124;&#4140;&#4152;&#4170; &#4125;&#4100;&#4153;&#4152;&#4114;&#4143;&#4141;&#4152; &#4121;&#4157;&#4140; &#4126;&#4143;&#4150;&#4152;&#4123;&#4112;&#4146;&#4244; &#4124;&#4096;&#4153;&#4096;&#4156;&#4096;&#4153;&#4117;&#4143;&#4150;&#4101;&#4150;&#4116;&#4146;&#4244; &#4112;&#4144;&#4112;&#4140;&#4096;&#4141;&#4143; &#4124;&#4143;&#4141;&#4097;&#4154;&#4100;&#4153;&#4112;&#4140;&#4117;&#4139;&#4170;

[http://ubuntuforums.org/showpost.php?p=12415248&postcount=10](http://ubuntuforums.org/showpost.php?p=12415248&postcount=10) 

&#4121;&#4157;&#4140; &#4222;&#4096;&#4106;&#4151;&#4153;&#4117;&#4139;&#4171; &#4124;&#4096;&#4153;&#4096;&#4156;&#4096;&#4153;&#4096; &#4145;&#4112;&#4140;&#4153;&#4145;&#4112;&#4140;&#4153;&#4145;&#4124;&#4152;&#4096;&#4141;&#4143; &#4112;&#4144;&#4117;&#4139;&#4112;&#4122;&#4153;&#4171; (&#4101;&#4140;&#4124;&#4150;&#4143;&#4152;&#4145;&#4117;&#4139;&#4100;&#4153;&#4152;&#4113;&#4140;&#4152;&#4112;&#4146;&#4151; &#4101;&#4140;&#4124;&#4150;&#4143;&#4152;&#4145;&#4112;&#4156; - &#4133;&#4117;&#4121;&#4140; - W, Q &#4112;&#4141;&#4143;&#4245;&#4121;&#4157;&#4140; &#4122;&#4117;&#4100;&#4151;&#4153; (  &#4154; )   (   &#4157; ) &#4112;&#4101;&#4153;&#4097;&#4143;&#4113;&#4146; &#4155;&#4118;&#4101;&#4153;&#4145;&#4116;&#4112;&#4140;&#4145;&#4124;&#4140;&#4096;&#4153;&#4117;&#4146; &#4096;&#4156;&#4146;&#4112;&#4122;&#4153; &#4113;&#4100;&#4153;&#4112;&#4140;&#4117;&#4146;&#4171; &#4129;&#4146;&#4114;&#4139;&#4145;&#4112;&#4156;&#4096;&#4124;&#4146; &#4162; &#4097;&#4139; &#4123;&#4141;&#4143;&#4096;&#4153;&#4124;&#4141;&#4143;&#4245; &#4123;&#4145;&#4112;&#4140;&#4151; &#4129;&#4102;&#4100;&#4153;&#4145;&#4155;&#4117;&#4121;&#4157;&#4140;&#4117;&#4139;&#4171;

> system setting --- keyboard layout &#4096;&#4143;&#4141; &#4126;&#4156;&#4140;&#4152;&#4223;&#4117;&#4142;&#4152; Burmese &#4096;&#4142;&#4152;&#4120;&#4143;&#4112;&#4153;&#4096;&#4143;&#4141; &#4145;&#4240;&#4156;&#4152;&#4223;&#4117;&#4142;&#4152; &#4155;&#4121;&#4116;&#4153;&#4121;&#4140;&#4124;&#4143;&#4141; &#4240;&#4143;&#4141;&#4096;&#4153;&#4124;&#4143;&#4141;&#4244; &#4123;&#4112;&#4140; &#4126;&#4141;&#4117;&#4139;&#4112;&#4122;&#4153;&#4170; &#4114;&#4139;&#4145;&#4117;&#4121;&#4146;&#4244; &#4129;&#4146;&#4114;&#4139;&#4096; Zawgyi One font &#4121;&#4127;&#4143;&#4112;&#4153;&#4117;&#4139;&#4120;&#4144;&#4152;&#4170;

Unicode - Myanmar 3 keyboard &#4117;&#4139;&#4171; Layout &#4096;&#4141;&#4143; [[COLOR="RoyalBlue"]&#4114;&#4142;&#4145;&#4116;&#4123;&#4140;&#4121;&#4157;&#4140;[/COLOR]]("http://commons.wikimedia.org/wiki/File:Myanmar3_Kayboard_Layout.jpg") &#4222;&#4096;&#4106;&#4151;&#4153;&#4117;&#4139;&#4171;  

> Libre &#4113;&#4146;&#4121;&#4157;&#4140; &#4101;&#4140;&#4240;&#4143;&#4141;&#4096;&#4153;&#4118;&#4143;&#4141;&#4244; Zawgyi One &#4096;&#4143;&#4141; &#4145;&#4240;&#4156;&#4152;&#4113;&#4140;&#4152;&#4145;&#4117;&#4121;&#4146;&#4244; &#4096;&#4142;&#4152;&#4120;&#4143;&#4112;&#4153; &#4096;&#4143;&#4141; us &#4096;&#4145;&#4116; my &#4096;&#4143;&#4141; &#4145;&#4240;&#4156;&#4152;&#4223;&#4117;&#4142;&#4152; &#4240;&#4143;&#4141;&#4096;&#4153;&#4124;&#4143;&#4141;&#4096;&#4153;&#4112;&#4146;&#4244; &#4129;&#4097;&#4139; &#4145;&#4240;&#4156;&#4152;&#4113;&#4140;&#4152;&#4112;&#4146;&#4244; Zawgyi One font &#4121;&#4127;&#4143;&#4112;&#4153;&#4145;&#4112;&#4140;&#4244;&#4120;&#4146; &#4112;&#4155;&#4097;&#4140;&#4152;&#4127;&#4140; &#4145;&#4155;&#4117;&#4140;&#4100;&#4153;&#4152;&#4126;&#4156;&#4140;&#4152;&#4117;&#4139;&#4112;&#4122;&#4153;&#4170; &#4129;&#4146;&#4126;&#4106;&#4153;&#4124;&#4143;&#4141; &#4121;&#4155;&#4118;&#4101;&#4153;&#4145;&#4129;&#4140;&#4100;&#4153;&#4170; MSWord &#4113;&#4146;&#4121;&#4157;&#4140; &#4145;&#4103;&#4140;&#4153;&#4098;&#4154;&#4142; &#4116;&#4146;&#4244; &#4240;&#4143;&#4141;&#4096;&#4153;&#4123;&#4126;&#4124;&#4143;&#4141; &#4240;&#4143;&#4141;&#4096;&#4153;&#4124;&#4143;&#4141;&#4244;&#4123;&#4121;&#4122;&#4153;&#4244; &#4116;&#4106;&#4153;&#4152;&#4124;&#4121;&#4153;&#4152;&#4121;&#4154;&#4141;&#4147;&#4152; &#4121;&#4240;&#4157;&#4141;&#4120;&#4144;&#4152;&#4124;&#4140;&#4152; &#4097;&#4100;&#4153;&#4119;&#4154;&#4140;...

CTL font &#4145;&#4155;&#4117;&#4140;&#4100;&#4153;&#4152;&#4145;&#4117;&#4152;&#4123;&#4100;&#4153; &#4123;&#4117;&#4139;&#4112;&#4122;&#4153;&#4171; Log In &#4125;&#4100;&#4153;&#4155;&#4117;&#4142;&#4152; &#4222;&#4096;&#4106;&#4151;&#4153;&#4117;&#4139;&#4171; &#4117;&#4150;&#4143;&#4155;&#4121;&#4100;&#4153;&#4123;&#4117;&#4139;&#4121;&#4122;&#4153;&#4171; 

Menu bar &#4096; Tools >> Options 
Language Settings &#4096;&#4141;&#4143; double click &#4124;&#4143;&#4117;&#4153;&#4117;&#4139;&#4171;
Languages &#4096;&#4141;&#4143; &#4239;&#4157;&#4141;&#4117;&#4153;&#4117;&#4139;&#4171; 
&#4106;&#4140;&#4118;&#4096;&#4153;&#4096; Default Languages for documents >> CTL &#4121;&#4157;&#4140; [none] &#4096;&#4141;&#4143; &#4145;&#4123;&#4156;&#4152;&#4117;&#4139;&#4171;

[Enhanced language support &#4121;&#4157;&#4140; Enable for complex text layout (CTL) &#4096;&#4141;&#4143; &#4129;&#4121;&#4157;&#4116;&#4153;&#4155;&#4097;&#4101;&#4153;&#4113;&#4140;&#4152;&#4123;&#4117;&#4139;&#4121;&#4122;&#4153;&#4171; &#4112;&#4096;&#4122;&#4153;&#4124;&#4141;&#4143;&#4245; CTL &#4145;&#4123;&#4156;&#4152;&#4124;&#4141;&#4143;&#4245; &#4121;&#4123;&#4123;&#4100;&#4153; &#4129;&#4145;&#4117;&#4186;&#4096; Locale Settings &#4121;&#4157;&#4140; Burmese &#4096;&#4141;&#4143; &#4145;&#4123;&#4156;&#4152;&#4145;&#4117;&#4152;&#4118;&#4141;&#4143;&#4245; &#4124;&#4141;&#4143;&#4145;&#4096;&#4140;&#4100;&#4153;&#4152;&#4124;&#4141;&#4143;&#4117;&#4139;&#4121;&#4122;&#4153;&#4171;]

CTL &#4121;&#4157;&#4140; [none] &#4096;&#4141;&#4143; &#4145;&#4123;&#4156;&#4152;&#4155;&#4117;&#4142;&#4152;&#4123;&#4100;&#4153; &#4120;&#4122;&#4153;&#4118;&#4096;&#4153;&#4096; LibreOffice Writer &#4096;&#4141;&#4143; double-click &#4124;&#4143;&#4117;&#4153;&#4117;&#4139;&#4171;
Basic Fonts (CTL) &#4096;&#4141;&#4143; &#4239;&#4157;&#4141;&#4117;&#4153;&#4155;&#4117;&#4142;&#4152; &#4106;&#4140;&#4118;&#4096;&#4153;&#4121;&#4157;&#4140; Zawgyi-One &#4096;&#4141;&#4143; &#4124;&#4141;&#4143;&#4126;&#4124;&#4141;&#4143; &#4145;&#4123;&#4156;&#4152;&#4145;&#4117;&#4152;&#4123;&#4150;&#4143;&#4117;&#4139;&#4171; 

&#4129;&#4102;&#4100;&#4151;&#4153;&#4145;&#4112;&#4156;&#4121;&#4157;&#4140; OK &#4239;&#4157;&#4141;&#4117;&#4153;&#4118;&#4141;&#4143;&#4245; &#4121;&#4145;&#4121;&#4151;&#4117;&#4139;&#4116;&#4146;&#4245;&#4171; &#4121;&#4127;&#4143;&#4112;&#4153;&#4123;&#4100;&#4153; Save &#4124;&#4143;&#4117;&#4153;&#4121;&#4157;&#4140; &#4121;&#4127;&#4143;&#4112;&#4153;&#4117;&#4139;&#4120;&#4144;&#4152;&#4171; 
&#4129;&#4140;&#4152;&#4124;&#4150;&#4143;&#4152;&#4155;&#4117;&#4142;&#4152;&#4123;&#4100;&#4153; &#4101;&#4141;&#4112;&#4153;&#4097;&#4154;&#4123;&#4100;&#4153;&#4145;&#4129;&#4140;&#4100;&#4153; LibreOffice &#4096;&#4141;&#4143; &#4112;&#4097;&#4154;&#4096;&#4153;&#4117;&#4141;&#4112;&#4153;&#4155;&#4117;&#4142;&#4152; &#4155;&#4117;&#4116;&#4153;&#4118;&#4156;&#4100;&#4151;&#4153;&#4117;&#4139;&#4171;
&#4155;&#4121;&#4116;&#4153;&#4121;&#4140;&#4124;&#4141;&#4143; &#4123;&#4141;&#4143;&#4096;&#4153;&#4124;&#4141;&#4143;&#4096;&#4153;&#4123;&#4100;&#4153; Zawgyi-One, English &#4102;&#4141;&#4143; &#4112;&#4155;&#4097;&#4140;&#4152; font &#4155;&#4118;&#4101;&#4153;&#4145;&#4116;&#4112;&#4140; &#4145;&#4112;&#4156;&#4245;&#4117;&#4139;&#4121;&#4122;&#4153;&#4171;
English font &#4096;&#4141;&#4143;&#4117;&#4139; &#4155;&#4117;&#4100;&#4153;&#4097;&#4154;&#4100;&#4153;&#4155;&#4117;&#4100;&#4153;&#4124;&#4141;&#4143;&#4245; &#4123;&#4117;&#4139;&#4112;&#4122;&#4153;&#4171; &#4114;&#4139;&#4145;&#4117;&#4121;&#4146;&#4151; &#4121;&#4124;&#4141;&#4143;&#4129;&#4117;&#4153;&#4117;&#4139;&#4120;&#4144;&#4152;&#4171;
CTL font &#4145;&#4155;&#4117;&#4140;&#4100;&#4153;&#4152;&#4112;&#4140;&#4116;&#4146;&#4245; &#4123;&#4117;&#4139;&#4112;&#4122;&#4153;&#4171; &#4116;&#4098;&#4141;&#4143; CTL &#4096; Hindi &#4124;&#4140;&#4152;&#4121;&#4126;&#4141;&#4120;&#4144;&#4152;&#4171; &#4114;&#4139;&#4145;&#4222;&#4096;&#4140;&#4100;&#4153;&#4151; &#4096;&#4142;&#4152;&#4120;&#4143;&#4112;&#4153;&#4145;&#4155;&#4117;&#4140;&#4100;&#4153;&#4152;&#4123;&#4100;&#4153; &#4145;&#4239;&#4157;&#4152;&#4126;&#4124;&#4141;&#4143;&#4155;&#4118;&#4101;&#4153;&#4112;&#4140;&#4170; &#4101;&#4140;&#4124;&#4150;&#4143;&#4152; &#4121;&#4157;&#4116;&#4153;&#4121;&#4157;&#4116;&#4153; &#4121;&#4155;&#4121;&#4100;&#4153;&#4112;&#4140; &#4155;&#4118;&#4101;&#4153;&#4112;&#4140;&#4117;&#4139;&#4171;

Unicode &#4126;&#4150;&#4143;&#4152;&#4123;&#4100;&#4153;&#4145;&#4112;&#4140;&#4151; CTL language &#4121;&#4157;&#4140; Burmese &#4124;&#4141;&#4143;&#4245; &#4145;&#4123;&#4156;&#4152;&#4112;&#4140;&#4116;&#4146;&#4245; Padauk &#4096;&#4141;&#4143; autodetect &#4124;&#4143;&#4117;&#4153;&#4117;&#4139;&#4112;&#4122;&#4153;&#4171;

---

### Post by MHK99 on 2013-04-26
I have a number of issues with Zawgyi/Padauk fonts. I have installed the two as advised in mm-deb pkg. And also taken the above steps. I still can not get the correct words. I will write zagyi below.

 [FONT=Zawgyi-One]&#4145;&#4103;&#4140;&#4154;&#4168;&#4155;&#4142;     Could you please help me get it right (for both zawgyi and Padauk).

Thank you.[/FONT]

---

### Post by MHK99 on 2013-05-13
[SIZE=4][FONT=Padauk Book]&#4096;&#4156;&#4106;&#4151;&#4154;&#4112;&#4140;&#4121;&#4117;&#4156;&#4106;&#4151;&#4154;&#4101;&#4143;&#4150;&#4124;&#4141;&#4143;&#4151;&#4117;&#4139;&#4171;&#4129;&#4097;&#4143;&#4121;&#4158;&#4126;&#4145;&#4126;&#4145;&#4097;&#4155;&#4140;&#4097;&#4155;&#4140; &#4120;&#4112;&#4154;&#4117;&#4156;&#4142;&#4152;&#4117;&#4156;&#4116;&#4154;&#4123;&#4141;&#4143;&#4096;&#4154;&#4112;&#4145;&#4140;&#4151;&#4121;&#4158;&#4116;&#4154;&#4126;&#4157;&#4140;&#4152;&#4117;&#4139;&#4117;&#4156;&#4142;[/FONT][/SIZE]

---

