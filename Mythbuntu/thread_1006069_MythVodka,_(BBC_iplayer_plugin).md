---
title: "MythVodka, (BBC iplayer plugin)"
date: 2008-12-08
forum: Mythbuntu
---

### Post by gneville on 2008-12-08
Hi All,

I am wondering if anyone has managed to get this new plugin working with Mythbuntu 8.04?

[http://www.mythtv.org/wiki/index.php/MythStreams]("http://www.mythtv.org/wiki/index.php/MythStreams")

I had troubles compling it, but after a while i managed to get a .so file and put that into my plugins directory and have edited the xml files, however when running the plugin it comes up saying "cannot locate "streamsui" in theme "stream-""
So not really sure what is wrong here. I have tried different themes (im just using the standard ones that come with mythbuntu)

I wonder if this can be packaged up into a .deb if someones successfully installed it?

Thanks

Graham

---

### Post by SiHa on 2008-12-09
Ooh, I'll certainly be having a go if get any time over the next week. iPlayer would be useful.

---

### Post by gneville on 2008-12-09
Found the issue with the error message.

I found that mythvokda came with its own "streams-ui.xml" file, which i then copied into the (current) themes directory for mythtv.

"/usr/share/mythtv/themes/Mythbuntu-8.04/"

---

### Post by gneville on 2008-12-09
Woo Hoo! After much playing around I have finally gotten this to work!

---

### Post by SiHa on 2008-12-09
And was it worth the effort?

---

### Post by SiHa on 2008-12-09
Well, I had a go, and the results have been less than optimal!

After finally managing to put (I think) the various bits in the right places (ie - not where the wiki says to put them) I at least goy Myth to try and run the plugin, but i get this error:```
2008-12-09 20:58:39.344 MythPlugin::init() dlerror: /usr/lib/mythtv/plugins/libmythvodka.so: wrong ELF class: ELFCLASS32
2008-12-09 20:58:39.344 Unable to initialize plugin 'mythvodka'.
2008-12-09 20:58:39.344 Unable to run plugin 'mythvodka': not initialized

```

ELFCLASS?

I mean - I know we're coming up to Christmas and all, but surely any class of elf should be able to do this stuff?

Does anyone know what this means? It's nothing to do with the fact that I'm running the AMD64 version of Ubuntu I suppose?

Edit: OK, I've searched on these forums (fora?) and this does indeed seem to be the problem - is there anything I can do about this, or should I just give up now - I'm not about to trash my Backend just so I can put the i386 version on and use iPlayer.

Or do plugins just need to be installed on the frontend? If so, my main frontend is i386...

TIA,

Simon

---

### Post by SiHa on 2008-12-12
Well, it seems to do something on a 32-bit install, although I'm still getting errors - think they're down to folders not being created. Hopfully I'll get a chance to investigate over the weekend. If I can get it going, I'll update the wiki for Mythbuntu 8.04: some of the file locations mentioned are wrong, and there's quite a bit missing (like remembering to make the get_iplayer script executable).

---

### Post by lerrup on 2008-12-15
I'm trying this and keep getting error messages when I'm building it, such as 

*** No rule to make target `/usr/qt/3/mkspecs/linux-g++/qmake.conf', needed by `Makefile'.

I think I have everything installed, any idea what I might be missing?

thanks.

---

### Post by SiHa on 2008-12-15
I think it's probably because there's another mythvodka subdirectory created. If you're in the first, it probably won't compile properly.

Here's what I had to do, I'm using Mythbuntu 8.04.1 (i386):

I've highlighted in [COLOR="Red"]red[/COLOR] where it's different from the wiki

```

[COLOR="Red"]cd /usr/share/mythtv[/COLOR]
wget http://www.bewhere.co.uk/mythvodka.04.tar.gz
tar xzf mythvodka.04.tar.gz
[COLOR="Red"]cd mythvodka/mythvodka[/COLOR]
rm Makefile [COLOR="red"](it was there for me)[/COLOR]
qmake mythvodka.pro
make
make install
[COLOR="Red"]cp ../scripts/* /usr/local/bin/[/COLOR]
wget http://www.linuxcentre.net/get_iplayer/get_iplayer[COLOR="red"]
sudo chmod a+x get_iplayer[/COLOR]
[COLOR="Red"]sudo[/COLOR] mv get_iplayer /usr/local/bin 
[COLOR="Red"]sudo mv /mythtv/plugins/libmythvodka.so /usr/lib/mythtv/plugins/libmythvodka.so[/COLOR]

```

There's a varable referenced in **Makefile** called **INSTALL ROOT**, but that seemed not to be correctly identified, I think that's the reason for the last line.

You also need to copy streams-ui.xml into the folder for the current theme you are using eg **/usr/share/mythtv/themes/blootube**
I notice there's also a streams-ui.xml in the themes-wide folder, I guess this is supposed to be used for a w/s theme, but I used the other (didn't notice this one at first) and it's OK.

library.xml & media_settings.xml were in /usr/share/mythtv, not /usr/local/share/mythtv as the wiki page suggests.

Oh, and ensure you have mplayer installed:oops:

It works!

The revision 3 stuff, for some reason has a delay on the video, so I needed to add a couple of key definitions to the mplayer lircrc:

```
begin
    prog = mplayer
    button = ArrowUp
    config = audio-delay 0.1
    repeat = 0
    delay = 0
end

begin
    prog = mplayer
    button = Arrowdown
    config = audio-delay -0.1
    repeat = 0
    delay = 0
end

```

I added **-audio-delay -0.4** into the commandline in **playstream.xml**, but it doesn't appear to do anything - I still need to manually adjust at the start of each video.

The iPlayer, at first appears not to work. Whatever title I select, I get the same one appering in the 'buffering' window, and the progress bar does nothing. After about 10s though, it plays. Not sure whether this is a problem with the get-iplayer script or maybe a premissions issue.

I'm prtty sure that's erverything I did to get it working

---

### Post by lerrup on 2008-12-15
thanks for the tips - I now have an application that seems to run.

Problem is all the streams don't seem to work and the buffering screen has a Russell Brand quote.  

Is it me or them?

---

### Post by SiHa on 2008-12-16
All the Rev3 & iPlayer streams seem to work for me (well, all the ones I've tried anyway), and I too get the same Russell Brand quote. I'm assuming that's a bug with the get_iplayer script, but I don't think I'm clever enough to debug it.

---

### Post by Ohs0Ahxi on 2008-12-16
Just had a go at installing this, things seemed to go smoothly but nothing will stream just get message pop up saying something along the lines of not available for streaming. 
I had a poke around the logs but nothing stood out, i can get it working from the terminal so im not sure where to start looking to see whats wrong in myth. Any ideas?

---

### Post by SiHa on 2008-12-16
Yes, the logging isn't terribly good. If something goes wrong, you just get the 'Sorry old bean...' message.

In the frontend log, for a Revision3 stream, you should have a line like this in your frontend log:```
 /usr/local/bin/playstream.sh /usr/bin/curl /usr/bin/mencoder http://www.podtrac.com/pts/redirect.avi/bitcast-a.bitgravity.com/revision3/web/diggreel/0048/diggreel--0048--steaming--large.xvid.avi
```

The first thing I did to debug was to paste the above directly into a terminal, and see what sort of errors I got. Chances are you're either missing a dependency (have you checked you have curl / mplayer?), or there's apermissions issue.

I have a vague memory of changing the permissions on /var/tmp, not sure though.

---

### Post by Ohs0Ahxi on 2008-12-16
I spotted some stuff in the logs about /var/tmp as well so i changed permissions just in case.
I hadn't upgraded to 8.10 so i just did that and it seems to have fixed it, possible a dependency, who knows.
Thanks for the suggestions

---

### Post by lerrup on 2008-12-16
> **SiHa said:**
> All the Rev3 & iPlayer streams seem to work for me (well, all the ones I've tried anyway), and I too get the same Russell Brand quote. I'm assuming that's a bug with the get_iplayer script, but I don't think I'm clever enough to debug it.

Its buried in streamsui.cpp if anyone is intrested in being able to use it in front of small children/grandparents.

---

### Post by hexag on 2008-12-26
hey guys,

i've just managed to get my myth box working! dvb-s n'everything, i'm dead chuffed & now is a time for expansion and improvement... now i've gotta have mythvodka, it's going to get foot stompy & princess wanting a pony style strop if i don't, but, *but*! Wait! The url is dead, i can find it nowhere, big sad face, tried everywhere, no torrent, rapidshare, newsgroup or other provider of legitimate software can help me out, google just has the one address, the one which is dead. 

can anyone help me out with a copy? please, oh it'd make my day, as i can spend the next couple of days pulling my hair out for something else instead & we can't have a relaxed & stress free holiday now, can we? hell, i'll be doing my lady's mythbox next week, i know how to have fun...

love n hugs n stuff,

hexag,

---

### Post by hexag on 2008-12-27
soz guys, the file's there again, just bad timing on my behalf!

---

### Post by vv1gg1 on 2008-12-30
Hello,

im the guy who wrote that plugin. theres a new version ready to go that uses the higher quality flash streams, and im currently working on Hulu support.

So yeah the install procedure isnt that great Sorry bout that. It works properly if you get the source for the standard mythplugins, build them to make sure youve got a sane environment, then unpack the mythvodka.tar.gz into the plugins dir. That way it picks up the same path as the rest of the plugins and will install properly.

Ill ty and fix some day. If youve any Qs leave em here.

---

### Post by nrune on 2009-01-03
errors in install?  

Make
```
root@mythtv:/usr/lib/mythtv/plugins/mythvodka/mythvodka# make
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT -fPIC  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_PLUGIN -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I../../../../../include/qt3 -o main.o main.cpp
main.cpp:1:32: error: mythtv/mythcontext.h: No such file or directory
main.cpp:2:30: error: mythtv/mythdbcon.h: No such file or directory
main.cpp:3:34: error: mythtv/mythpluginapi.h: No such file or directory
In file included from main.cpp:5:
streamsui.h:4:32: error: mythtv/mythdialogs.h: No such file or directory
In file included from main.cpp:6:
streamssettings.h:4:29: error: mythtv/settings.h: No such file or directory
In file included from main.cpp:5:
streamsui.h:13: error: expected class-name before ‘{’ token
streamsui.h:14: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
streamsui.h:15: error: expected ‘;’ before ‘public’
streamsui.h:18: error: expected `)' before ‘*’ token
streamsui.h:23: error: ‘QKeyEvent’ has not been declared
streamsui.h:32: error: ISO C++ forbids declaration of ‘GenericTree’ with no type
streamsui.h:32: error: expected ‘;’ before ‘*’ token
streamsui.h:33: error: ISO C++ forbids declaration of ‘GenericTree’ with no type
streamsui.h:33: error: expected ‘;’ before ‘*’ token
streamsui.h:35: error: ‘QDomNode’ has not been declared
streamsui.h:36: error: ‘QDomNode’ has not been declared
streamsui.h:43: error: ISO C++ forbids declaration of ‘GenericTree’ with no type
streamsui.h:43: error: expected ‘;’ before ‘*’ token
streamsui.h:44: error: ISO C++ forbids declaration of ‘UIManagedTreeListType’ with no type
streamsui.h:44: error: expected ‘;’ before ‘*’ token
streamsui.h:45: error: ISO C++ forbids declaration of ‘GenericTree’ with no type
streamsui.h:45: error: expected ‘;’ before ‘*’ token
streamsui.h:50: error: ISO C++ forbids declaration of ‘MSqlQuery’ with no type
streamsui.h:50: error: expected ‘;’ before ‘*’ token
streamsui.h:51: error: ISO C++ forbids declaration of ‘MSqlQuery’ with no type
streamsui.h:51: error: expected ‘;’ before ‘*’ token
streamsui.h:52: error: ISO C++ forbids declaration of ‘MSqlQuery’ with no type
streamsui.h:52: error: expected ‘;’ before ‘*’ token
streamsui.h:56: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:56: error: expected ‘;’ before ‘*’ token
streamsui.h:57: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:57: error: expected ‘;’ before ‘*’ token
streamsui.h:58: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:58: error: expected ‘;’ before ‘*’ token
streamsui.h:59: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:59: error: expected ‘;’ before ‘*’ token
streamsui.h:60: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:60: error: expected ‘;’ before ‘*’ token
streamsui.h:61: error: ISO C++ forbids declaration of ‘UIImageType’ with no type
streamsui.h:61: error: expected ‘;’ before ‘*’ token
streamsui.h:62: error: ISO C++ forbids declaration of ‘MythPopupBox’ with no type
streamsui.h:62: error: expected ‘;’ before ‘*’ token
streamsui.h:63: error: ISO C++ forbids declaration of ‘MythPopupBox’ with no type
streamsui.h:63: error: expected ‘;’ before ‘*’ token
streamsui.h:64: error: ISO C++ forbids declaration of ‘MythPopupBox’ with no type
streamsui.h:64: error: expected ‘;’ before ‘*’ token
streamsui.h:65: error: ISO C++ forbids declaration of ‘QButton’ with no type
streamsui.h:65: error: expected ‘;’ before ‘*’ token
streamsui.h:66: error: ISO C++ forbids declaration of ‘QButton’ with no type
streamsui.h:66: error: expected ‘;’ before ‘*’ token
streamsui.h:71: error: expected `:' before ‘slots’
streamsui.h:72: error: expected primary-expression before ‘void’
streamsui.h:72: error: ISO C++ forbids declaration of ‘slots’ with no type
streamsui.h:72: error: expected ‘;’ before ‘void’
streamsui.h:73: error: ‘IntVector’ has not been declared
streamsui.h:75: error: expected `:' before ‘slots’
streamsui.h:76: error: expected primary-expression before ‘void’
streamsui.h:76: error: ISO C++ forbids declaration of ‘slots’ with no type
streamsui.h:76: error: expected ‘;’ before ‘void’
In file included from main.cpp:6:
streamssettings.h:7: error: expected class-name before ‘{’ token
main.cpp:10: error: expected constructor, destructor, or type conversion before ‘*’ token
main.cpp: In function ‘int mythplugin_init(const char*)’:
main.cpp:20: error: ‘gContext’ was not declared in this scope
main.cpp:21: error: ‘MYTH_BINARY_VERSION’ was not declared in this scope
main.cpp:23: error: ‘VB_IMPORTANT’ was not declared in this scope
main.cpp:24: error: ‘VERBOSE’ was not declared in this scope
main.cpp:30: error: ‘VB_IMPORTANT’ was not declared in this scope
main.cpp:31: error: ‘VERBOSE’ was not declared in this scope
main.cpp: In function ‘void runStreams()’:
main.cpp:40: error: ‘gContext’ was not declared in this scope
streamsui.h:20: error: ‘StreamsUI::~StreamsUI()’ is private
main.cpp:41: error: within this context
main.cpp:42: error: ‘class StreamsUI’ has no member named ‘exec’
main.cpp: In function ‘void runConfig()’:
main.cpp:49: error: ‘class StreamsSettings’ has no member named ‘exec’
main.cpp: In function ‘int mythplugin_run()’:
main.cpp:54: error: ‘gContext’ was not declared in this scope
main.cpp:65: error: ‘VB_IMPORTANT’ was not declared in this scope
main.cpp:66: error: ‘VERBOSE’ was not declared in this scope
main.cpp: In function ‘int setupDatabase()’:
main.cpp:85: error: ‘gContext’ was not declared in this scope
main.cpp:88: error: ‘gContext’ was not declared in this scope
main.cpp:90: error: ‘VB_GENERAL’ was not declared in this scope
main.cpp:90: error: ‘VERBOSE’ was not declared in this scope
main.cpp:92: error: ‘MSqlQuery’ was not declared in this scope
main.cpp:92: error: expected `;' before ‘query’
main.cpp:93: error: ‘query’ was not declared in this scope
main.cpp:126: error: ‘VB_IMPORTANT’ was not declared in this scope
main.cpp:138: error: ‘VB_IMPORTANT’ was not declared in this scope
make: *** [main.o] Error 1

```

make install
```
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT -fPIC  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_PLUGIN -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I../../../../../include/qt3 -o main.o main.cpp
main.cpp:1:32: error: mythtv/mythcontext.h: No such file or directory
main.cpp:2:30: error: mythtv/mythdbcon.h: No such file or directory
main.cpp:3:34: error: mythtv/mythpluginapi.h: No such file or directory
In file included from main.cpp:5:
streamsui.h:4:32: error: mythtv/mythdialogs.h: No such file or directory
In file included from main.cpp:6:
streamssettings.h:4:29: error: mythtv/settings.h: No such file or directory
In file included from main.cpp:5:
streamsui.h:13: error: expected class-name before ‘{’ token
streamsui.h:14: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
streamsui.h:15: error: expected ‘;’ before ‘public’
streamsui.h:18: error: expected `)' before ‘*’ token
streamsui.h:23: error: ‘QKeyEvent’ has not been declared
streamsui.h:32: error: ISO C++ forbids declaration of ‘GenericTree’ with no type
streamsui.h:32: error: expected ‘;’ before ‘*’ token
streamsui.h:33: error: ISO C++ forbids declaration of ‘GenericTree’ with no type
streamsui.h:33: error: expected ‘;’ before ‘*’ token
streamsui.h:35: error: ‘QDomNode’ has not been declared
streamsui.h:36: error: ‘QDomNode’ has not been declared
streamsui.h:43: error: ISO C++ forbids declaration of ‘GenericTree’ with no type
streamsui.h:43: error: expected ‘;’ before ‘*’ token
streamsui.h:44: error: ISO C++ forbids declaration of ‘UIManagedTreeListType’ with no type
streamsui.h:44: error: expected ‘;’ before ‘*’ token
streamsui.h:45: error: ISO C++ forbids declaration of ‘GenericTree’ with no type
streamsui.h:45: error: expected ‘;’ before ‘*’ token
streamsui.h:50: error: ISO C++ forbids declaration of ‘MSqlQuery’ with no type
streamsui.h:50: error: expected ‘;’ before ‘*’ token
streamsui.h:51: error: ISO C++ forbids declaration of ‘MSqlQuery’ with no type
streamsui.h:51: error: expected ‘;’ before ‘*’ token
streamsui.h:52: error: ISO C++ forbids declaration of ‘MSqlQuery’ with no type
streamsui.h:52: error: expected ‘;’ before ‘*’ token
streamsui.h:56: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:56: error: expected ‘;’ before ‘*’ token
streamsui.h:57: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:57: error: expected ‘;’ before ‘*’ token
streamsui.h:58: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:58: error: expected ‘;’ before ‘*’ token
streamsui.h:59: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:59: error: expected ‘;’ before ‘*’ token
streamsui.h:60: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:60: error: expected ‘;’ before ‘*’ token
streamsui.h:61: error: ISO C++ forbids declaration of ‘UIImageType’ with no type
streamsui.h:61: error: expected ‘;’ before ‘*’ token
streamsui.h:62: error: ISO C++ forbids declaration of ‘MythPopupBox’ with no type
streamsui.h:62: error: expected ‘;’ before ‘*’ token
streamsui.h:63: error: ISO C++ forbids declaration of ‘MythPopupBox’ with no type
streamsui.h:63: error: expected ‘;’ before ‘*’ token
streamsui.h:64: error: ISO C++ forbids declaration of ‘MythPopupBox’ with no type
streamsui.h:64: error: expected ‘;’ before ‘*’ token
streamsui.h:65: error: ISO C++ forbids declaration of ‘QButton’ with no type
streamsui.h:65: error: expected ‘;’ before ‘*’ token
streamsui.h:66: error: ISO C++ forbids declaration of ‘QButton’ with no type
streamsui.h:66: error: expected ‘;’ before ‘*’ token
streamsui.h:71: error: expected `:' before ‘slots’
streamsui.h:72: error: expected primary-expression before ‘void’
streamsui.h:72: error: ISO C++ forbids declaration of ‘slots’ with no type
streamsui.h:72: error: expected ‘;’ before ‘void’
streamsui.h:73: error: ‘IntVector’ has not been declared
streamsui.h:75: error: expected `:' before ‘slots’
streamsui.h:76: error: expected primary-expression before ‘void’
streamsui.h:76: error: ISO C++ forbids declaration of ‘slots’ with no type
streamsui.h:76: error: expected ‘;’ before ‘void’
In file included from main.cpp:6:
streamssettings.h:7: error: expected class-name before ‘{’ token
main.cpp:10: error: expected constructor, destructor, or type conversion before ‘*’ token
main.cpp: In function ‘int mythplugin_init(const char*)’:
main.cpp:20: error: ‘gContext’ was not declared in this scope
main.cpp:21: error: ‘MYTH_BINARY_VERSION’ was not declared in this scope
main.cpp:23: error: ‘VB_IMPORTANT’ was not declared in this scope
main.cpp:24: error: ‘VERBOSE’ was not declared in this scope
main.cpp:30: error: ‘VB_IMPORTANT’ was not declared in this scope
main.cpp:31: error: ‘VERBOSE’ was not declared in this scope
main.cpp: In function ‘void runStreams()’:
main.cpp:40: error: ‘gContext’ was not declared in this scope
streamsui.h:20: error: ‘StreamsUI::~StreamsUI()’ is private
main.cpp:41: error: within this context
main.cpp:42: error: ‘class StreamsUI’ has no member named ‘exec’
main.cpp: In function ‘void runConfig()’:
main.cpp:49: error: ‘class StreamsSettings’ has no member named ‘exec’
main.cpp: In function ‘int mythplugin_run()’:
main.cpp:54: error: ‘gContext’ was not declared in this scope
main.cpp:65: error: ‘VB_IMPORTANT’ was not declared in this scope
main.cpp:66: error: ‘VERBOSE’ was not declared in this scope
main.cpp: In function ‘int setupDatabase()’:
main.cpp:85: error: ‘gContext’ was not declared in this scope
main.cpp:88: error: ‘gContext’ was not declared in this scope
main.cpp:90: error: ‘VB_GENERAL’ was not declared in this scope
main.cpp:90: error: ‘VERBOSE’ was not declared in this scope
main.cpp:92: error: ‘MSqlQuery’ was not declared in this scope
main.cpp:92: error: expected `;' before ‘query’
main.cpp:93: error: ‘query’ was not declared in this scope
main.cpp:126: error: ‘VB_IMPORTANT’ was not declared in this scope
main.cpp:138: error: ‘VB_IMPORTANT’ was not declared in this scope
make: *** [main.o] Error 1

```

What am I missing??

---

### Post by nrune on 2009-01-03
Okay so I am running a 64 bit system and that seems to be the error.  Any way to fix this?

Thanks

---

### Post by Dubstar_04 on 2009-01-03
you need to download all the mythtv 0.21 sourcecode and build the plugin from within the tree once you have configured mythtv and mythtvplugins.

it should build on 64 bit no problem then

---

### Post by Dubstar_04 on 2009-01-03
> **vv1gg1 said:**
> Hello,

im the guy who wrote that plugin. theres a new version ready to go that uses the higher quality flash streams, and im currently working on Hulu support.

So yeah the install procedure isnt that great Sorry bout that. It works properly if you get the source for the standard mythplugins, build them to make sure youve got a sane environment, then unpack the mythvodka.tar.gz into the plugins dir. That way it picks up the same path as the rest of the plugins and will install properly.

Ill ty and fix some day. If youve any Qs leave em here.

Thanks for working on this plugin.

iplayer won't work for me. All the listing are there but they won't play. As other people have mentioned I get a message saying someone slept with my granddaughter then one saying sorry old bean. 

Revision 3 works fine so i assume it is all installed correctly.

---

### Post by SiHa on 2009-01-03
I'll second that, thanks for writing the plugin, yes it has it's issues, but it's a darned better than anything I'd be able to knock up!

---

### Post by puno on 2009-01-04
A great plugin and now workiing on my system but..

I tried to update my iplayer feed this morning and it crashes the frontend. I have investigated and discovered the following:

1. The call to the grabber is successful and xml is returned.

2. When processing the xml it throws up the following

     "Error: letter is expected Location Line 2229 Column 20"

3. Checking Line 2229 Column 20 there is a & symbol in the Title of the programme.

4. As a temp fix I've edited the method "populateDatabasefromGrabber" in the streamsui.cpp file and removed the exit(-1) which stops the frontend from exiting but it means processing of the xml also stops at the offending line and any further programmes are not shown.


Is there a proper fix for this?

Thanks

Rich

---

### Post by vv1gg1 on 2009-01-04
Hi,

yep BBC put a title with an & into there show list, and that breaks my plugin. Grumble. Never saw that coming.

ill fix the plugin but for now edit get_iplayer and add an extra line on 3125  with "${name} =~ s/\&//g ;" to change it from this:

print XML "<movie title=\"${title}\">
                                                                <video><url id=\"p1\">${pid}.mov<playlist/></url></video>
                                                                <info><description>${desc}</description></info>
                                                        </movie>\n" if $opt{fxd};
print XML "\t\t<Name>$name</Name>\n\t\t<Url>${pid}.mov</Url>\n\t\t<Subtitle>${episode}</Subtitle>\n\t\t<Synopsis>${desc}</Synopsis>\n" if $opt{mythtv};


to this:

print XML "<movie title=\"${title}\">
                                                            <video><url id=\"p1\">${pid}.mov<playlist/></url></video>
                                                                <info><description>${desc}</description></info>
                                                        </movie>\n" if $opt{fxd};
${name} =~ s/\&//g ;
print XML "\t\t<Name>$name</Name>\n\t\t<Url>${pid}.mov</Url>\n\t\t<Subtitle>${episode}</Subtitle>\n\t\t<Synopsis>${desc}</Synopsis>\n" if $opt{mythtv};

Also, the hulu integration is done, video of it working at:
[http://uk.youtube.com/watch?v=LuZIyhnPNnc](http://uk.youtube.com/watch?v=LuZIyhnPNnc)

check wiki for more info. I use it in UK by having a cheap VPS in America (needs hardly any memory so should cost less than £5 amonth easily), then you can install the included php script, hulu script and rtmpump and then it gets the content over RTMP from the states and streams it as an flv over http so its fast.

---

### Post by managementboy on 2009-01-04
tried you plugin like described here. I have a 64 bit system runing the latest 0.21-fixes. When I start Myth Vodka I get the following segfault:

```
2009-01-04 15:18:57.141 MSqlQuery: INSERT INTO streams_streams (streamname, rating, runningtime, streamurl, type, subtitle, synopsis, streamimage, category) values ('Dance Lessons with Prager', '', '', 'http://www.podtrac.com/pts/redirect.avi/bitcast-a.bitgravity.com/revision3/web/diggnation/0161/diggnation--0161--2008-07-31cwalk--large.xvid.avi', 'http', 'Fri, 01 Aug 2008 23:00:00 GMT', '
Jaw Dropping Dance Moves, Blogger gets check from HP for declining Vista EULA, New Search Engine: Cuil, Steve Jobs'' Life not in Danger, Rumor: Google to buy Digg.
      ', '
Jaw Dropping Dance Moves, Blogger gets check from HP for declining Vista EULA, New Search Engine: Cuil, Steve Jobs'' Life not in Danger, Rumor: Google to buy Digg.
      ', '')
2009-01-04 15:18:57.141 MSqlQuery: SELECT LAST_INSERT_ID();
2009-01-04 15:18:57.141 getHttp: grabbing: 'file:'
2009-01-04 15:18:57.141 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-04 15:18:57.141 done: 0 bytes
2009-01-04 15:18:57.151 Server returned an error status code 0 for url:
2009-01-04 15:18:57.151 Got 0 bytes from url: ''
2009-01-04 15:18:57.152 MythFlix: Failed to download image from:
2009-01-04 15:18:57.152 MythFlix: Finished copying boxshot file from server ()
2009-01-04 15:18:57.152 MSqlQuery: INSERT INTO streams_showtimes (feedid, streamid, showtimes) values (8, 195, '')
2009-01-04 15:18:57.152 MSqlQuery: SELECT id FROM streams_streams Where streamname = 'Pirates!'
2009-01-04 15:18:57.153 MSqlQuery: INSERT INTO streams_streams (streamname, rating, runningtime, streamurl, type, subtitle, synopsis, streamimage, category) values ('Pirates!', '', '', 'http://www.podtrac.com/pts/redirect.avi/bitcast-a.bitgravity.com/revision3/web/diggnation/0160/diggnation--0160--2008-07-24joshv--large.xvid.avi', 'http', 'Fri, 25 Jul 2008 23:00:00 GMT', '
The Pirate Bay Wants to Encrypt the Entire Internet,  B-2 Stealth Bomber Crash Scene Photos, Anheuser Busch Sold for 50 Billion, Can''t Find a Parking Spot? Check Smartphone, Pirates Download More Music.
      ', '
The Pirate Bay Wants to Encrypt the Entire Internet,  B-2 Stealth Bomber Crash Scene Photos, Anheuser Busch Sold for 50 Billion, Can''t Find a Parking Spot? Check Smartphone, Pirates Download More Music.
      ', '')
2009-01-04 15:18:57.153 MSqlQuery: SELECT LAST_INSERT_ID();
2009-01-04 15:18:57.153 getHttp: grabbing: 'file:'
2009-01-04 15:18:57.153 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-04 15:18:57.153 done: 0 bytes
2009-01-04 15:18:57.164 Server returned an error status code 0 for url:
2009-01-04 15:18:57.164 Got 0 bytes from url: ''
2009-01-04 15:18:57.164 MythFlix: Failed to download image from:
2009-01-04 15:18:57.164 MythFlix: Finished copying boxshot file from server ()
2009-01-04 15:18:57.164 MSqlQuery: INSERT INTO streams_showtimes (feedid, streamid, showtimes) values (8, 196, '')
2009-01-04 15:18:57.165 MSqlQuery: SELECT id FROM streams_streams Where streamname = 'Kevin and Alex Take Over Martin''s Shed '
2009-01-04 15:18:57.165 MSqlQuery: INSERT INTO streams_streams (streamname, rating, runningtime, streamurl, type, subtitle, synopsis, streamimage, category) values ('Kevin and Alex Take Over Martin''s Shed ', '', '', 'http://www.podtrac.com/pts/redirect.avi/bitcast-a.bitgravity.com/revision3/web/diggnation/0159/diggnation--0159--2008-07-18maubrowncow--large.xvid.avi', 'http', 'Fri, 18 Jul 2008 23:00:00 GMT', '
Kevin and Alex have invaded Martin Sargent''s Shed!  Watch them discuss these stories: New Radiohead Video with Lasers,  iPhone OS 2.0 Unlocked, Apple Customers Insulted by Reporter and they Strike Back, Comcast Ordered to Stop BitTorrent Interference, Brett Favre is mad at the Packers
      ', '
Kevin and Alex have invaded Martin Sargent''s Shed!  Watch them discuss these stories: New Radiohead Video with Lasers,  iPhone OS 2.0 Unlocked, Apple Customers Insulted by Reporter and they Strike Back, Comcast Ordered to Stop BitTorrent Interference, Brett Favre is mad at the Packers
      ', '')
2009-01-04 15:18:57.165 MSqlQuery: SELECT LAST_INSERT_ID();
2009-01-04 15:18:57.165 getHttp: grabbing: 'file:'
2009-01-04 15:18:57.166 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-04 15:18:57.166 done: 0 bytes
2009-01-04 15:18:57.176 Server returned an error status code 0 for url:
2009-01-04 15:18:57.176 Got 0 bytes from url: ''
2009-01-04 15:18:57.176 SSDP::ProcessData - requestLine: M-SEARCH * HTTP/1.1
2009-01-04 15:18:57.176 SSDP::ProcessSearchrequest : [upnp:rootdevice] MX=0
2009-01-04 15:18:57.176 MythFlix: Failed to download image from:
2009-01-04 15:18:57.176 MythFlix: Finished copying boxshot file from server ()
2009-01-04 15:18:57.177 MSqlQuery: INSERT INTO streams_showtimes (feedid, streamid, showtimes) values (8, 197, '')
2009-01-04 15:18:57.177 getHttp: grabbing: 'http://bitcast-a.bitgravity.com/revision3/images/shows/diggnation/diggnation.jpg'
2009-01-04 15:18:57.177 HttpComms::stateChanged: connecting (2)
2009-01-04 15:18:57.250 HttpComms::stateChanged: sending (3)
2009-01-04 15:18:57.312 HttpComms::stateChanged: reading (4)
2009-01-04 15:18:57.312 Got HTTP response: 200:OK
2009-01-04 15:18:57.312 Keys: accept-ranges,content-length,content-type,date,etag,last-modified,server
2009-01-04 15:18:57.586 HttpComms::stateChanged: connected (5)
2009-01-04 15:18:57.586 done: 96124 bytes
2009-01-04 15:18:57.596 getHttpFile: saving to file: '/var/tmp/mythvod/Diggnation'
2009-01-04 15:18:57.596 getHttpFile: File saved OK
2009-01-04 15:18:57.596 Got 96124 bytes from url: 'http://bitcast-a.bitgravity.com/revision3/images/shows/diggnation/diggnation.jpg'
Segmentation fault

```

I run the plugin from germany.

---

### Post by nrune on 2009-01-04
```
you need to download all the mythtv 0.21 sourcecode 
```

got it

```
and build the plugin from within the tree once you have configured mythtv and mythtvplugins.
```

Not a clue how to do this, can you point me in the right direction?

Thanks

---

### Post by Neon Dusk on 2009-01-04
Thanks for the plugin - got it working in 8.10 x64

Couldn't get the 0.5 version working (with the higher quality flvs) as playiplayer.sh was looking for 'iplayerdump.partial.mov' (should of been iplayerdump.partial.mp4.flv). 

Once that was fixed mencoder complained about the missing wmv9 codecs (not sure if possible to get these codecs installed on a x64 system). Went back to 0.4 and it seems ok

---

### Post by njolin on 2009-01-04
Thanks for the fix above,  it seems to work now, but stops playing after a few mins.

Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame


Exiting... (End of file)
2009-01-04 20:09:37.743 Selection: File: [http://www.podtrac.com/pts/redirect.avi/bitcast-a.bitgravity.com/revision3/web/diggreel/0051/diggreel--0051--2k8top10--large.xvid.avi](http://www.podtrac.com/pts/redirect.avi/bitcast-a.bitgravity.com/revision3/web/diggreel/0051/diggreel--0051--2k8top10--large.xvid.avi)
b

---

### Post by vv1gg1 on 2009-01-06
Hi,

good work, the get_iplayer script picks its output filename differently for rtmp streams. In the latest version .07 ive included a modified script, should work fine and give you a better quality stream

---

### Post by vv1gg1 on 2009-01-06
if it bombs out after a few mins most probably a bandwidth issue :| or your net conn dropping.

---

### Post by Neon Dusk on 2009-01-06
> **vv1gg1 said:**
> Hi,

good work, the get_iplayer script picks its output filename differently for rtmp streams. In the latest version .07 ive included a modified script, should work fine and give you a better quality stream

Thanks I'll check it out. It seems that the get_iplayer rtmp streams fail to convert on ubuntu due to ffmpeg being out of date (some comments [here](http://linuxcentre.net/get_iplayer-gets-high-quality-flash-bbc-iplayer-rtmp-downloading-capability/#comments))

---

### Post by august495 on 2009-01-06
> **nrune said:**
> ```
you need to download all the mythtv 0.21 sourcecode 
```

got it

```
and build the plugin from within the tree once you have configured mythtv and mythtvplugins.
```

Not a clue how to do this, can you point me in the right direction?

Thanks

Did you figure this out? I am in the same spot.

---

### Post by Neon Dusk on 2009-01-07
Once you have the mythplugins source and have installed the build dependencies you should be able to build MythVodka.

You'll also need curl and mencoder installed.

---

### Post by nrune on 2009-01-07
> Did you figure this out? I am in the same spot. 

Nope. 

I am really wanting to run Boxee, and because of some other upgrades to the system, migrating mysql etc, I am moving to 32 bit sometime this week. I have not installed on my 32bit low power frontend, andI may try that out this weekend. Assuming that the backend/frontend upgrade goes well. 

Best of luck
Mike

---

### Post by theophile on 2009-01-08
> **nrune said:**
> errors in install?  

Make
```
root@mythtv:/usr/lib/mythtv/plugins/mythvodka/mythvodka# make
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT -fPIC  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_PLUGIN -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I../../../../../include/qt3 -o main.o main.cpp
main.cpp:1:32: error: mythtv/mythcontext.h: No such file or directory
main.cpp:2:30: error: mythtv/mythdbcon.h: No such file or directory
main.cpp:3:34: error: mythtv/mythpluginapi.h: No such file or directory
In file included from main.cpp:5:
streamsui.h:4:32: error: mythtv/mythdialogs.h: No such file or directory
In file included from main.cpp:6:
streamssettings.h:4:29: error: mythtv/settings.h: No such file or directory
In file included from main.cpp:5:
streamsui.h:13: error: expected class-name before ‘{’ token
streamsui.h:14: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
streamsui.h:15: error: expected ‘;’ before ‘public’
streamsui.h:18: error: expected `)' before ‘*’ token
streamsui.h:23: error: ‘QKeyEvent’ has not been declared
streamsui.h:32: error: ISO C++ forbids declaration of ‘GenericTree’ with no type
streamsui.h:32: error: expected ‘;’ before ‘*’ token
streamsui.h:33: error: ISO C++ forbids declaration of ‘GenericTree’ with no type
streamsui.h:33: error: expected ‘;’ before ‘*’ token
streamsui.h:35: error: ‘QDomNode’ has not been declared
streamsui.h:36: error: ‘QDomNode’ has not been declared
streamsui.h:43: error: ISO C++ forbids declaration of ‘GenericTree’ with no type
streamsui.h:43: error: expected ‘;’ before ‘*’ token
streamsui.h:44: error: ISO C++ forbids declaration of ‘UIManagedTreeListType’ with no type
streamsui.h:44: error: expected ‘;’ before ‘*’ token
streamsui.h:45: error: ISO C++ forbids declaration of ‘GenericTree’ with no type
streamsui.h:45: error: expected ‘;’ before ‘*’ token
streamsui.h:50: error: ISO C++ forbids declaration of ‘MSqlQuery’ with no type
streamsui.h:50: error: expected ‘;’ before ‘*’ token
streamsui.h:51: error: ISO C++ forbids declaration of ‘MSqlQuery’ with no type
streamsui.h:51: error: expected ‘;’ before ‘*’ token
streamsui.h:52: error: ISO C++ forbids declaration of ‘MSqlQuery’ with no type
streamsui.h:52: error: expected ‘;’ before ‘*’ token
streamsui.h:56: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:56: error: expected ‘;’ before ‘*’ token
streamsui.h:57: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:57: error: expected ‘;’ before ‘*’ token
streamsui.h:58: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:58: error: expected ‘;’ before ‘*’ token
streamsui.h:59: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:59: error: expected ‘;’ before ‘*’ token
streamsui.h:60: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:60: error: expected ‘;’ before ‘*’ token
streamsui.h:61: error: ISO C++ forbids declaration of ‘UIImageType’ with no type
streamsui.h:61: error: expected ‘;’ before ‘*’ token
streamsui.h:62: error: ISO C++ forbids declaration of ‘MythPopupBox’ with no type
streamsui.h:62: error: expected ‘;’ before ‘*’ token
streamsui.h:63: error: ISO C++ forbids declaration of ‘MythPopupBox’ with no type
streamsui.h:63: error: expected ‘;’ before ‘*’ token
streamsui.h:64: error: ISO C++ forbids declaration of ‘MythPopupBox’ with no type
streamsui.h:64: error: expected ‘;’ before ‘*’ token
streamsui.h:65: error: ISO C++ forbids declaration of ‘QButton’ with no type
streamsui.h:65: error: expected ‘;’ before ‘*’ token
streamsui.h:66: error: ISO C++ forbids declaration of ‘QButton’ with no type
streamsui.h:66: error: expected ‘;’ before ‘*’ token
streamsui.h:71: error: expected `:' before ‘slots’
streamsui.h:72: error: expected primary-expression before ‘void’
streamsui.h:72: error: ISO C++ forbids declaration of ‘slots’ with no type
streamsui.h:72: error: expected ‘;’ before ‘void’
streamsui.h:73: error: ‘IntVector’ has not been declared
streamsui.h:75: error: expected `:' before ‘slots’
streamsui.h:76: error: expected primary-expression before ‘void’
streamsui.h:76: error: ISO C++ forbids declaration of ‘slots’ with no type
streamsui.h:76: error: expected ‘;’ before ‘void’
In file included from main.cpp:6:
streamssettings.h:7: error: expected class-name before ‘{’ token
main.cpp:10: error: expected constructor, destructor, or type conversion before ‘*’ token
main.cpp: In function ‘int mythplugin_init(const char*)’:
main.cpp:20: error: ‘gContext’ was not declared in this scope
main.cpp:21: error: ‘MYTH_BINARY_VERSION’ was not declared in this scope
main.cpp:23: error: ‘VB_IMPORTANT’ was not declared in this scope
main.cpp:24: error: ‘VERBOSE’ was not declared in this scope
main.cpp:30: error: ‘VB_IMPORTANT’ was not declared in this scope
main.cpp:31: error: ‘VERBOSE’ was not declared in this scope
main.cpp: In function ‘void runStreams()’:
main.cpp:40: error: ‘gContext’ was not declared in this scope
streamsui.h:20: error: ‘StreamsUI::~StreamsUI()’ is private
main.cpp:41: error: within this context
main.cpp:42: error: ‘class StreamsUI’ has no member named ‘exec’
main.cpp: In function ‘void runConfig()’:
main.cpp:49: error: ‘class StreamsSettings’ has no member named ‘exec’
main.cpp: In function ‘int mythplugin_run()’:
main.cpp:54: error: ‘gContext’ was not declared in this scope
main.cpp:65: error: ‘VB_IMPORTANT’ was not declared in this scope
main.cpp:66: error: ‘VERBOSE’ was not declared in this scope
main.cpp: In function ‘int setupDatabase()’:
main.cpp:85: error: ‘gContext’ was not declared in this scope
main.cpp:88: error: ‘gContext’ was not declared in this scope
main.cpp:90: error: ‘VB_GENERAL’ was not declared in this scope
main.cpp:90: error: ‘VERBOSE’ was not declared in this scope
main.cpp:92: error: ‘MSqlQuery’ was not declared in this scope
main.cpp:92: error: expected `;' before ‘query’
main.cpp:93: error: ‘query’ was not declared in this scope
main.cpp:126: error: ‘VB_IMPORTANT’ was not declared in this scope
main.cpp:138: error: ‘VB_IMPORTANT’ was not declared in this scope
make: *** [main.o] Error 1

```

make install
```
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT -fPIC  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_PLUGIN -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I../../../../../include/qt3 -o main.o main.cpp
main.cpp:1:32: error: mythtv/mythcontext.h: No such file or directory
main.cpp:2:30: error: mythtv/mythdbcon.h: No such file or directory
main.cpp:3:34: error: mythtv/mythpluginapi.h: No such file or directory
In file included from main.cpp:5:
streamsui.h:4:32: error: mythtv/mythdialogs.h: No such file or directory
In file included from main.cpp:6:
streamssettings.h:4:29: error: mythtv/settings.h: No such file or directory
In file included from main.cpp:5:
streamsui.h:13: error: expected class-name before ‘{’ token
streamsui.h:14: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
streamsui.h:15: error: expected ‘;’ before ‘public’
streamsui.h:18: error: expected `)' before ‘*’ token
streamsui.h:23: error: ‘QKeyEvent’ has not been declared
streamsui.h:32: error: ISO C++ forbids declaration of ‘GenericTree’ with no type
streamsui.h:32: error: expected ‘;’ before ‘*’ token
streamsui.h:33: error: ISO C++ forbids declaration of ‘GenericTree’ with no type
streamsui.h:33: error: expected ‘;’ before ‘*’ token
streamsui.h:35: error: ‘QDomNode’ has not been declared
streamsui.h:36: error: ‘QDomNode’ has not been declared
streamsui.h:43: error: ISO C++ forbids declaration of ‘GenericTree’ with no type
streamsui.h:43: error: expected ‘;’ before ‘*’ token
streamsui.h:44: error: ISO C++ forbids declaration of ‘UIManagedTreeListType’ with no type
streamsui.h:44: error: expected ‘;’ before ‘*’ token
streamsui.h:45: error: ISO C++ forbids declaration of ‘GenericTree’ with no type
streamsui.h:45: error: expected ‘;’ before ‘*’ token
streamsui.h:50: error: ISO C++ forbids declaration of ‘MSqlQuery’ with no type
streamsui.h:50: error: expected ‘;’ before ‘*’ token
streamsui.h:51: error: ISO C++ forbids declaration of ‘MSqlQuery’ with no type
streamsui.h:51: error: expected ‘;’ before ‘*’ token
streamsui.h:52: error: ISO C++ forbids declaration of ‘MSqlQuery’ with no type
streamsui.h:52: error: expected ‘;’ before ‘*’ token
streamsui.h:56: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:56: error: expected ‘;’ before ‘*’ token
streamsui.h:57: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:57: error: expected ‘;’ before ‘*’ token
streamsui.h:58: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:58: error: expected ‘;’ before ‘*’ token
streamsui.h:59: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:59: error: expected ‘;’ before ‘*’ token
streamsui.h:60: error: ISO C++ forbids declaration of ‘UITextType’ with no type
streamsui.h:60: error: expected ‘;’ before ‘*’ token
streamsui.h:61: error: ISO C++ forbids declaration of ‘UIImageType’ with no type
streamsui.h:61: error: expected ‘;’ before ‘*’ token
streamsui.h:62: error: ISO C++ forbids declaration of ‘MythPopupBox’ with no type
streamsui.h:62: error: expected ‘;’ before ‘*’ token
streamsui.h:63: error: ISO C++ forbids declaration of ‘MythPopupBox’ with no type
streamsui.h:63: error: expected ‘;’ before ‘*’ token
streamsui.h:64: error: ISO C++ forbids declaration of ‘MythPopupBox’ with no type
streamsui.h:64: error: expected ‘;’ before ‘*’ token
streamsui.h:65: error: ISO C++ forbids declaration of ‘QButton’ with no type
streamsui.h:65: error: expected ‘;’ before ‘*’ token
streamsui.h:66: error: ISO C++ forbids declaration of ‘QButton’ with no type
streamsui.h:66: error: expected ‘;’ before ‘*’ token
streamsui.h:71: error: expected `:' before ‘slots’
streamsui.h:72: error: expected primary-expression before ‘void’
streamsui.h:72: error: ISO C++ forbids declaration of ‘slots’ with no type
streamsui.h:72: error: expected ‘;’ before ‘void’
streamsui.h:73: error: ‘IntVector’ has not been declared
streamsui.h:75: error: expected `:' before ‘slots’
streamsui.h:76: error: expected primary-expression before ‘void’
streamsui.h:76: error: ISO C++ forbids declaration of ‘slots’ with no type
streamsui.h:76: error: expected ‘;’ before ‘void’
In file included from main.cpp:6:
streamssettings.h:7: error: expected class-name before ‘{’ token
main.cpp:10: error: expected constructor, destructor, or type conversion before ‘*’ token
main.cpp: In function ‘int mythplugin_init(const char*)’:
main.cpp:20: error: ‘gContext’ was not declared in this scope
main.cpp:21: error: ‘MYTH_BINARY_VERSION’ was not declared in this scope
main.cpp:23: error: ‘VB_IMPORTANT’ was not declared in this scope
main.cpp:24: error: ‘VERBOSE’ was not declared in this scope
main.cpp:30: error: ‘VB_IMPORTANT’ was not declared in this scope
main.cpp:31: error: ‘VERBOSE’ was not declared in this scope
main.cpp: In function ‘void runStreams()’:
main.cpp:40: error: ‘gContext’ was not declared in this scope
streamsui.h:20: error: ‘StreamsUI::~StreamsUI()’ is private
main.cpp:41: error: within this context
main.cpp:42: error: ‘class StreamsUI’ has no member named ‘exec’
main.cpp: In function ‘void runConfig()’:
main.cpp:49: error: ‘class StreamsSettings’ has no member named ‘exec’
main.cpp: In function ‘int mythplugin_run()’:
main.cpp:54: error: ‘gContext’ was not declared in this scope
main.cpp:65: error: ‘VB_IMPORTANT’ was not declared in this scope
main.cpp:66: error: ‘VERBOSE’ was not declared in this scope
main.cpp: In function ‘int setupDatabase()’:
main.cpp:85: error: ‘gContext’ was not declared in this scope
main.cpp:88: error: ‘gContext’ was not declared in this scope
main.cpp:90: error: ‘VB_GENERAL’ was not declared in this scope
main.cpp:90: error: ‘VERBOSE’ was not declared in this scope
main.cpp:92: error: ‘MSqlQuery’ was not declared in this scope
main.cpp:92: error: expected `;' before ‘query’
main.cpp:93: error: ‘query’ was not declared in this scope
main.cpp:126: error: ‘VB_IMPORTANT’ was not declared in this scope
main.cpp:138: error: ‘VB_IMPORTANT’ was not declared in this scope
make: *** [main.o] Error 1

```

What am I missing??

I have the same problem, I am NOT un AMD64, and I am installing this from the source tree created by 'apt-get source mythplugins'

What's the way to make this work?

---

### Post by grytpype on 2009-01-08
Does anyone have a working binary for AMD64 that they can make available?

---

### Post by briangig on 2009-01-08
tips:

make sure you have libmyth-dev installed..

also, get the plugins source:

apt-get source mythplugins

and make sure you have the dependencies listed on the wiki, and follow the instructions on page one of this thread...

i think I got mine working, can't seem to get past "updating listings".  let it sit over night and it looked like there was an error message scrolling infinitely.

---

### Post by theophile on 2009-01-08
> **briangig said:**
> tips:

make sure you have libmyth-dev installed..
That was what I was missing. It now builds and installs properly.

> i think I got mine working, can't seem to get past "updating listings".  let it sit over night and it looked like there was an error message scrolling infinitely.
But now I'm in the same boat. All my paths are correct but when I go to MythVodka, it says "updating listings" for a moment then the entire frontend crashes revealing these errors:

```
2009-01-08 09:41:11.411 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-08 09:41:11.421 Server returned an error status code 0 for url: 
2009-01-08 09:41:11.424 Inserting prog: 1st Taping of Pixel Perfect at the Revision3 Studio
2009-01-08 09:41:11.426 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-08 09:41:11.436 Server returned an error status code 0 for url: 
2009-01-08 09:41:11.439 Inserting prog: The One Where Sarah Meets Brad Pitt?
2009-01-08 09:41:11.442 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-08 09:41:11.452 Server returned an error status code 0 for url: 
2009-01-08 09:41:11.455 Inserting prog: Studio Audio Improvements and the set of Internet Superstar
2009-01-08 09:41:11.457 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-08 09:41:11.469 Server returned an error status code 0 for url: 
2009-01-08 09:41:11.471 Inserting prog: St. Louis Diggnation Randomness
2009-01-08 09:41:11.474 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-08 09:41:11.484 Server returned an error status code 0 for url: 
2009-01-08 09:41:11.487 Inserting prog: Content Delivery Delivered
2009-01-08 09:41:11.489 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-08 09:41:11.499 Server returned an error status code 0 for url: 
2009-01-08 09:41:11.502 Inserting prog: Progress is Next To Godliness!
2009-01-08 09:41:11.504 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-08 09:41:11.515 Server returned an error status code 0 for url: 
2009-01-08 09:41:11.517 Inserting prog: Behind the Browser: Revision3.com
2009-01-08 09:41:11.520 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-08 09:41:11.530 Server returned an error status code 0 for url: 
2009-01-08 09:41:11.533 Inserting prog: Rev3 Studio Operations
2009-01-08 09:41:11.535 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-08 09:41:11.545 Server returned an error status code 0 for url: 
2009-01-08 09:41:11.548 Inserting prog: VC Baby
2009-01-08 09:41:11.550 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-08 09:41:11.561 Server returned an error status code 0 for url: 
2009-01-08 09:41:11.563 Inserting prog: A Thousand Thanks
2009-01-08 09:41:11.566 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-08 09:41:11.576 Server returned an error status code 0 for url: 
2009-01-08 09:41:11.578 Inserting prog: The Sound and The Fury
2009-01-08 09:41:11.581 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-08 09:41:11.593 Server returned an error status code 0 for url: 
2009-01-08 09:41:11.595 Inserting prog: This Place is a Mess!
2009-01-08 09:41:11.597 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-08 09:41:11.608 Server returned an error status code 0 for url: 
2009-01-08 09:41:11.610 Inserting prog: The Fruit Club Council
2009-01-08 09:41:11.613 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-08 09:41:11.623 Server returned an error status code 0 for url: 
2009-01-08 09:41:11.626 Inserting prog: Behind the Infection
2009-01-08 09:41:11.628 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-08 09:41:11.639 Server returned an error status code 0 for url: 
2009-01-08 09:41:11.641 Inserting prog: It's Party Time!
2009-01-08 09:41:11.644 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-08 09:41:11.655 Server returned an error status code 0 for url: 
2009-01-08 09:41:11.658 Inserting prog: It's a Beautiful Day in the Neighborhood
2009-01-08 09:41:11.660 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-08 09:41:11.670 Server returned an error status code 0 for url: 
2009-01-08 09:41:11.686 MythVodka Data Grabber: Executing '/usr/local/bin/get_iplayer -q --mythtv - --xml-channels'
2009-01-08 09:41:13.190 Grabber Finished. Processing Data.
2009-01-08 09:41:13.237 Error parsing data from grabber: Error: letter is expected Location Line: 2436 Column 20

```

...and so on. Any ideas?

---

### Post by Neon Dusk on 2009-01-08
The last error is because there is an unencoded & in the XML from the get_iplayer script.

Follow vv1gg1 instructions in post [post=6491280]25[/post] of this thread. N.B. Depending on your get_iplayer script version the line numbers may be different but if you search for '<Name>$name' you should find the correct location.

---

### Post by briangig on 2009-01-08
well i ran gethulu.pl manually, and let it run while i am at work...will see.  there was an error that popped up occasionally...will see what it was when i get home, something about line 115-118.

---

### Post by theophile on 2009-01-08
Okay, got it running. For me the key to getting Hulu to work was 'apt-get install python-beautifulsoup'.

It's working great, though I can't get the BBC content. Also there seem to be some bugs in the Hulu script. Movies show up under the TV show sub menu and if you go to a movie it displays episodes from unrelated TV shows instead of the movie.

All in all, it's very functional and I really, REALLY hope it continues to be developed. It's very good!! Thanks!

---

### Post by briangig on 2009-01-08
OK, i decided the try and run it manually, like the wiki said 'gethulu.pl /var/tmp/hulu.xml', then 'cat gethulu.pl /var/tmp/hulu.xml', there were a few errors i saw when gethulu.pl was run, something about lines 115-118.  Anyway, it finished, but it didnt do anything, Still says "Updating listings", and stuck at 40%.

---

### Post by theophile on 2009-01-08
When I did it, it took nearly an hour for the initial command to generate the xml file. Then I changed the grabber command to "/bin/cat /var/tmp/hulu.xml" and it took maybe 20 minutes to import all the listings. You can see it all scroll by on the frontend command line. After that, it only takes a second or two to reload. All the Hulu content worked great after that.

---

### Post by briangig on 2009-01-08
i thought i needed to do something about the grabber command...i assume something in the menu or something?  thanks

---

### Post by theophile on 2009-01-09
Yeah, just change the Hulu grabber command to: 
```
/bin/cat /var/tmp/hulu.xml
```
That way it's just reading the results of the script previously run rather than running it all over again. Even so, it takes a while the first time you run it. Switch to console view to see progress. It stays on 40% for a very, very long time.

---

### Post by briangig on 2009-01-09
hah...wish i had seen that.  i found the grabber setting in the menu...changed it over and it just sat there for 40%...so i decided to rebuild the xml file.  doh!  oh well, thanks for the help.

---

### Post by briangig on 2009-01-09
wow...can't believe it's working!  Rev3 is the only one i tried, but its working...all i care.  seems like the audio is out of sync.

In addition had to chmod a+x mythvodgrabber.pl and playstream.sh

hulu needed BeautifulSoup, rtmpdump (which needed boost libraries).  Damn...but it is working!  I was afraid my little 1.6Ghz Atom processor wouldnt be able to handle it, but its very smooth.  nice job on the project...but really, whats with the obscene quotes?

---

### Post by theophile on 2009-01-09
> **briangig said:**
> ...but really, whats with the obscene quotes?
Yeah, no kidding. Some people actually have families and don't just watch TV endlessly in their parents' basement. I think this is the first time in 10 years of using open source software that I've ever seen profanities put directly into the UI like that. Wow...

---

### Post by bmwman on 2009-01-10
Is it possible for somebody to make a .DEB for MythVodka?

---

### Post by vv1gg1 on 2009-01-10
> **bmwman said:**
> Is it possible for somebody to make a .DEB for MythVodka?
Yes, yes it is

[https://launchpad.net/~danser/+archive](https://launchpad.net/~danser/+archive)

---

### Post by bmwman on 2009-01-10
> **vv1gg1 said:**
> Yes, yes it is

[https://launchpad.net/~danser/+archive](https://launchpad.net/~danser/+archive)

Great. Is this going too work with 8.04 though? I upgraded one of my machines to 8.10 and had so many issues so I decided to keep 8.04 on my main backend/frontend machine.

Thanks

---

### Post by nrune on 2009-01-10
Trying mythvodka out on my low power 32bit frontend.  ran into this. 

```
2009-01-10 20:03:30.259 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-10 20:03:30.270 Server returned an error status code 0 for url: 
2009-01-10 20:03:30.316 MythVodka Data Grabber: Executing '/usr/share/mythtv/mythvodka/get_iplayer -q --mythtv - --xml-channels'
2009-01-10 20:03:31.860 Grabber Finished. Processing Data.
2009-01-10 20:03:31.893 Error parsing data from grabber: Error: letter is expected Location Line: 2358 Column 20

```

And then crashes the entire frontend

Pages of 
```
2009-01-10 20:03:30.259 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-10 20:03:30.270 Server returned an error status code 0 for url:
```

Install from the deb, help please.

---

### Post by vv1gg1 on 2009-01-11
> **nrune said:**
> Trying mythvodka out on my low power 32bit frontend.  ran into this. 

```
2009-01-10 20:03:30.259 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-10 20:03:30.270 Server returned an error status code 0 for url: 
2009-01-10 20:03:30.316 MythVodka Data Grabber: Executing '/usr/share/mythtv/mythvodka/get_iplayer -q --mythtv - --xml-channels'
2009-01-10 20:03:31.860 Grabber Finished. Processing Data.
2009-01-10 20:03:31.893 Error parsing data from grabber: Error: letter is expected Location Line: 2358 Column 20

```

And then crashes the entire frontend

Pages of 
```
2009-01-10 20:03:30.259 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-10 20:03:30.270 Server returned an error status code 0 for url:
```

Install from the deb, help please.

The get_iplayer script included in version .04 outputs bad XML. grab the latest release and take the get_iplayer script from that, its been modified to output slightly less evil XML that doesnt kill myth (but still not real XML).

---

### Post by marc.aronson on 2009-01-11
vv1gg1, this is great stuff! I've gotten it to work on my knoppmyth R5.5 install but I ran into one problem I wanted to let you know about. If one exits the playback of a video before it is finished by hitting escape, the rtmpdump job continues to execute. If you then start another show, a second rtmpdump job starts up. After a bit of testing, I found that I had 5 of these jobs running in parallel. Is there a way you could kill off the rtmpdump job if the user terminates viewing of the video?

I've created an ugly work around by making the following change to "/usr/local/bin/hulu":

1. At the bottom of /usr/local/bin/hulu I see the line 
[INDENT]os.system(command)[/INDENT]

2. I added 2 lines prior to that line. The 3 lines together now look like this:
[INDENT]os.system("pkill rtmpdump")[/INDENT]
[INDENT]os.system("sleep 2")[/INDENT]
[INDENT]os.system(command) [/INDENT]

This ensures that the first rtmpdump job is killed off before a new one can begin.

Marc

---

### Post by tzoom84 on 2009-01-12
I noticed around line 1009 of streamsui.cpp, there is the command:
```
argsStream += "/usr/local/bin/creatempeg.sh";
```

creatempeg.sh wasn't packed with the release, nor can I find it anywhere. Where can I find this? I believe this may be why *a certain feature* of MythVodka is not working for me right now

---

### Post by AdamA817 on 2009-01-13
I am attempting to install mythvodka and I make it through all the steps without error (compiled, installed, moved files in the right places, setup hulu for the local xml file), however when I try to go into mythvodka I get the following:

```
2009-01-13 19:03:33.734 XMLParse::LoadTheme using /usr/share/mythtv/themes/blootube-wide/streams-ui.xml
2009-01-13 19:03:33.942 streamsui.o: Couldn't find text area ratingvalue
2009-01-13 19:03:33.942 streamsui.o: Couldn't find text area showtimesvalue
2009-01-13 19:03:33.942 streamsui.o: Couldn't find image area feedname
2009-01-13 19:03:33.943 New DB connection, total: 4
2009-01-13 19:03:33.943 Connected to database 'mythconverg' at host: localhost
2009-01-13 19:03:33.953 Rows: 14
2009-01-13 19:03:33.984 Rows: 15
2009-01-13 19:03:34.000 Rows: 179
2009-01-13 19:03:34.181 Rows: 389
2009-01-13 19:03:34.604 Rows: 2
```

Then my frontend crashes.  If I try again it does the same thing. Any ideas where to look for the problem?

Thanks for the help, I am looking forward to being able to use this!

Update: I should mention, the first time I went in it did go through adding all of the shows into the db.  The process failed once, but when I went back in it seemed to continue the process until it hit the failure above.

Update 2: Here is the segfault from dmesg
```
[14724.872158] mythfrontend.re[13216]: segfault at d0 ip 00007f220a0e2bfe sp 00007fff16e40960 error 4 in libqt-mt.so.3.3.8[7f2209ab8000+80d000]
```

---

### Post by tgm4883 on 2009-01-13
Using MythVodka 07, and rtmpdump 1.3, I get everything compiled and installed, I use the local hulu.xml file that I have created.  My frontend always crashes when trying to get into mythvodka.  I'm not sure if this is an error with how i'm packaging this or whether it's something else.  I'm using the packages from here if you want to take a look  [https://edge.launchpad.net/~tgm4883/+archive](https://edge.launchpad.net/~tgm4883/+archive)

I've encluded the frontend log from a terminal when this happens.

---

### Post by gizmobay on 2009-01-14
> **AdamA817 said:**
> I am attempting to install mythvodka and I make it through all the steps without error (compiled, installed, moved files in the right places, setup hulu for the local xml file), however when I try to go into mythvodka I get the following:

```
2009-01-13 19:03:33.734 XMLParse::LoadTheme using /usr/share/mythtv/themes/blootube-wide/streams-ui.xml
2009-01-13 19:03:33.942 streamsui.o: Couldn't find text area ratingvalue
2009-01-13 19:03:33.942 streamsui.o: Couldn't find text area showtimesvalue
2009-01-13 19:03:33.942 streamsui.o: Couldn't find image area feedname
2009-01-13 19:03:33.943 New DB connection, total: 4
2009-01-13 19:03:33.943 Connected to database 'mythconverg' at host: localhost
2009-01-13 19:03:33.953 Rows: 14
2009-01-13 19:03:33.984 Rows: 15
2009-01-13 19:03:34.000 Rows: 179
2009-01-13 19:03:34.181 Rows: 389
2009-01-13 19:03:34.604 Rows: 2
```

Then my frontend crashes.  If I try again it does the same thing. Any ideas where to look for the problem?

Thanks for the help, I am looking forward to being able to use this!

Update: I should mention, the first time I went in it did go through adding all of the shows into the db.  The process failed once, but when I went back in it seemed to continue the process until it hit the failure above.

Update 2: Here is the segfault from dmesg
```
[14724.872158] mythfrontend.re[13216]: segfault at d0 ip 00007f220a0e2bfe sp 00007fff16e40960 error 4 in libqt-mt.so.3.3.8[7f2209ab8000+80d000]
```

I'm having the same exact problem and I can't figure out why.

---

### Post by vv1gg1 on 2009-01-14
> **tgm4883 said:**
> Using MythVodka 07, and rtmpdump 1.3, I get everything compiled and installed, I use the local hulu.xml file that I have created.  My frontend always crashes when trying to get into mythvodka.  I'm not sure if this is an error with how i'm packaging this or whether it's something else.  I'm using the packages from here if you want to take a look  [https://edge.launchpad.net/~tgm4883/+archive](https://edge.launchpad.net/~tgm4883/+archive)

I've encluded the frontend log from a terminal when this happens.

Again this is the issue with the BBC iPlayer script get_iplayer sending out rubbish XML. You should be able to either delete the command from the config file to stop it from running or use the included get_iplayer prog instead of the real one.

For the record the bug is that the get_iplayer script isnt doing &amp; instead of & in the XML

Anyone else seeing this in there log file has the same problem:

2009-01-13 17:31:01.633 MythVodka Data Grabber: Executing '/usr/bin/get_iplayer -q --mythtv - --xml-channels'
2009-01-13 17:31:02.155 Grabber Finished. Processing Data.
2009-01-13 17:31:02.186 Error parsing data from grabber: Error: letter is expected Location Line: 2463 Column 20

For anyone else with issues post what you see on screen, if it breaks on the updating data 20%, 40% screen then its usually shoddy XML causing it to fall over. Will fix this so it coeps a little better in the future.

Also, the first time you load run the update script it downloads all the show images, hence taking 40 mins to run the first time. After that it checks if the image exists, if it does it wont download do future updates are much quicker.

And for whoever asked ill dig out the creatempeg.sh script, it basically downloads the nzb, when the first file is done runs unrar reading in the first file and piping to mencoder that creates the mpeg, meanwhile myth waits for an mpeg of decent size to appear and plays when it can. Dont expect this to be flawless, as NZBs often have missing parts and you cant par em until all available data has arrived the results arnt great. I did write a more clever NZB parser that uses a few scripts to check that all parts are available on the usenet server before adding it to the myth menu, but this is a s l o w process... depends how important it is having the latest releases on the menu, or how much you care about hammering your userner server

---

### Post by Neon Dusk on 2009-01-14
> **AdamA817 said:**
> I am attempting to install mythvodka and I make it through all the steps without error (compiled, installed, moved files in the right places, setup hulu for the local xml file), however when I try to go into mythvodka I get the following:

```
2009-01-13 19:03:33.734 XMLParse::LoadTheme using /usr/share/mythtv/themes/blootube-wide/streams-ui.xml
2009-01-13 19:03:33.942 streamsui.o: Couldn't find text area ratingvalue
2009-01-13 19:03:33.942 streamsui.o: Couldn't find text area showtimesvalue
2009-01-13 19:03:33.942 streamsui.o: Couldn't find image area feedname
2009-01-13 19:03:33.943 New DB connection, total: 4
2009-01-13 19:03:33.943 Connected to database 'mythconverg' at host: localhost
2009-01-13 19:03:33.953 Rows: 14
2009-01-13 19:03:33.984 Rows: 15
2009-01-13 19:03:34.000 Rows: 179
2009-01-13 19:03:34.181 Rows: 389
2009-01-13 19:03:34.604 Rows: 2
```

...


That error suggests that you've got the wrong version of streams-ui.xml. If I remember correctly (I'm away from my Myth PC at the moment) there's one in mythvodka/ & another in mythvodka/mythvoda/themes/ - it should be the one in mythvodka/mythvoda/themes/ that you use.

---

### Post by AdamA817 on 2009-01-14
> **Neon Dusk said:**
> That error suggests that you've got the wrong version of streams-ui.xml. If I remember correctly (I'm away from my Myth PC at the moment) there's one in mythvodka/ & another in mythvodka/mythvoda/themes/ - it should be the one in mythvodka/mythvoda/themes/ that you use.

I am away from my myth box right now too, but I ssh'ed into the box and diffing the files it looks like I took the streams-ui.xml file from mythvodka/theme-wide/ instead of mythvodka/mythvodka/theme-wide/.  I copied over the file from the correct location, but I won't be able to test it until this evening.  I will update once I have had a chance to test.  Thanks.

Update: this did the trick!  I am now able to watch hulu content.

---

### Post by tgm4883 on 2009-01-14
> **vv1gg1 said:**
> Again this is the issue with the BBC iPlayer script get_iplayer sending out rubbish XML. You should be able to either delete the command from the config file to stop it from running or use the included get_iplayer prog instead of the real one.

For the record the bug is that the get_iplayer script isnt doing &amp; instead of & in the XML

Anyone else seeing this in there log file has the same problem:

2009-01-13 17:31:01.633 MythVodka Data Grabber: Executing '/usr/bin/get_iplayer -q --mythtv - --xml-channels'
2009-01-13 17:31:02.155 Grabber Finished. Processing Data.
2009-01-13 17:31:02.186 Error parsing data from grabber: Error: letter is expected Location Line: 2463 Column 20

For anyone else with issues post what you see on screen, if it breaks on the updating data 20%, 40% screen then its usually shoddy XML causing it to fall over. Will fix this so it coeps a little better in the future.

Also, the first time you load run the update script it downloads all the show images, hence taking 40 mins to run the first time. After that it checks if the image exists, if it does it wont download do future updates are much quicker.

And for whoever asked ill dig out the creatempeg.sh script, it basically downloads the nzb, when the first file is done runs unrar reading in the first file and piping to mencoder that creates the mpeg, meanwhile myth waits for an mpeg of decent size to appear and plays when it can. Dont expect this to be flawless, as NZBs often have missing parts and you cant par em until all available data has arrived the results arnt great. I did write a more clever NZB parser that uses a few scripts to check that all parts are available on the usenet server before adding it to the myth menu, but this is a s l o w process... depends how important it is having the latest releases on the menu, or how much you care about hammering your userner server

Fixed that issue, still can't get it to work though.  It starts importing a bunch of shows, every once in a while I get this type of error

```
2009-01-14 09:55:41.784 Inserting prog: The Astral Traveler
2009-01-14 09:55:43.405 Inserting prog: The Mechanical Men
2009-01-14 09:56:03.410 HttpComms::Timeout for url: http://thumbnails.hulu.com/7/56/7157_145x80_manicured__rALtRd77LUOuMUY5BlUUhw.jpg
2009-01-14 09:56:03.420 Server returned an error status code 0 for url: http://thumbnails.hulu.com/7/56/7157_145x80_manicured__rALtRd77LUOuMUY5BlUUhw.jpg
2009-01-14 09:56:03.420 HttpComms::done() - NetworkOperation Error on Finish: Request aborted (1): url: 'http://thumbnails.hulu.com/7/56/7157_145x80_manicured__rALtRd77LUOuMUY5BlUUhw.jpg'
2009-01-14 09:56:03.430 Inserting prog: The Phantom Family
2009-01-14 09:56:04.019 Inserting prog: Trip Through The Robot

```

Then it will continue importing shows.  It did eventually die though ending with this

```
2009-01-14 09:56:28.848 Inserting prog: Welcome Stranger
2009-01-14 09:56:29.343 Inserting prog: The Hungry Sea
2009-01-14 09:56:49.823 HttpComms::Timeout for url: http://assets.hulu.com/shows/show_thumbnail_lost_in_space.jpg
2009-01-14 09:56:49.834 Server returned an error status code 0 for url: http://assets.hulu.com/shows/show_thumbnail_lost_in_space.jpg
2009-01-14 09:56:49.834 HttpComms::done() - NetworkOperation Error on Finish: Request aborted (1): url: 'http://assets.hulu.com/shows/show_thumbnail_lost_in_space.jpg'
Segmentation fault

```

---

### Post by AdamA817 on 2009-01-14
> **tgm4883 said:**
> Fixed that issue, still can't get it to work though.  It starts importing a bunch of shows, every once in a while I get this type of error

```
2009-01-14 09:55:41.784 Inserting prog: The Astral Traveler
2009-01-14 09:55:43.405 Inserting prog: The Mechanical Men
2009-01-14 09:56:03.410 HttpComms::Timeout for url: http://thumbnails.hulu.com/7/56/7157_145x80_manicured__rALtRd77LUOuMUY5BlUUhw.jpg
2009-01-14 09:56:03.420 Server returned an error status code 0 for url: http://thumbnails.hulu.com/7/56/7157_145x80_manicured__rALtRd77LUOuMUY5BlUUhw.jpg
2009-01-14 09:56:03.420 HttpComms::done() - NetworkOperation Error on Finish: Request aborted (1): url: 'http://thumbnails.hulu.com/7/56/7157_145x80_manicured__rALtRd77LUOuMUY5BlUUhw.jpg'
2009-01-14 09:56:03.430 Inserting prog: The Phantom Family
2009-01-14 09:56:04.019 Inserting prog: Trip Through The Robot

```

Then it will continue importing shows.  It did eventually die though ending with this

```
2009-01-14 09:56:28.848 Inserting prog: Welcome Stranger
2009-01-14 09:56:29.343 Inserting prog: The Hungry Sea
2009-01-14 09:56:49.823 HttpComms::Timeout for url: http://assets.hulu.com/shows/show_thumbnail_lost_in_space.jpg
2009-01-14 09:56:49.834 Server returned an error status code 0 for url: http://assets.hulu.com/shows/show_thumbnail_lost_in_space.jpg
2009-01-14 09:56:49.834 HttpComms::done() - NetworkOperation Error on Finish: Request aborted (1): url: 'http://assets.hulu.com/shows/show_thumbnail_lost_in_space.jpg'
Segmentation fault

```

I realize it isn't a solution but I hit the same sort of thing, and if I started again it seemed to pickup where it left off (maybe?) and eventually finish successfully. (I think I had it fail twice).  I assumed that it was a network error, but I am not sure.

---

### Post by tsx_5 on 2009-01-15
Hi,

has anyone seen this error:

QHttp: empty path requested is invalid -- using '/'
2009-01-12 21:21:11.073 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: ''
2009-01-12 21:21:11.083 Server returned an error status code 0 for url: 


I see it directly after the plugin finishes downloading the Hulu stuff...  I think it may have something to do with the lack of thumbnail pictures for the hulu content.

Anyone have a clue on this?

---

### Post by tgm4883 on 2009-01-15
If we cron the get_hulu job, wouldn't it make sense to also cron the job that adds all these programs to the db (the part that happens when you go into mythvodka) or have the get_hulu job put these in there itself (or some wrapper script)?

I can't see needing this to happen on every frontend.

---

### Post by gneville on 2009-01-16
Hello All,

I have created this Wiki page which I created for people who have problems compiling mythvodka. Hope it helps.

[http://nevillehome.co.uk/dokuwiki/doku.php?id=mythbuntu:bbc_iplayer_mythvokda](http://nevillehome.co.uk/dokuwiki/doku.php?id=mythbuntu:bbc_iplayer_mythvokda)

Cheers

---

### Post by Dubstar_04 on 2009-01-17
Thats a great how to for people. 

I have one pointer. The streams-ui.xml file should be transfered into the default folder /usr/share/mythtv/themes/default. that way it will work with every theme. 

Thanks,

Dan

---

### Post by jamlam on 2009-01-17
Anyone know of a working download link for this? The ones listed in this thread all appear to be down...

---

### Post by penbrock on 2009-01-17
> **gneville said:**
> Hello All,

I have created this Wiki page which I created for people who have problems compiling mythvodka. Hope it helps.

[http://nevillehome.co.uk/dokuwiki/doku.php?id=mythbuntu:bbc_iplayer_mythvokda](http://nevillehome.co.uk/dokuwiki/doku.php?id=mythbuntu:bbc_iplayer_mythvokda)

Cheers

That was great, Thank you , thank you, thank you

How ever I do have one problem. 
When I go to apt-get install libmyth-dev I get
```

The following packages have unmet dependencies:
  libmyth-dev: Depends: libmyth-0.21-0 (= 0.21.0+fixes19693-0ubuntu0+mythbuntu1) but 0.21.0+fixes18722-0ubuntu1 is to be installed
E: Broken packages

``` 

Any ideas how I can get past this? I have done update/upgrade and upgraded a number og the mythtv files this morning before starting on this.

---

### Post by bah1976 on 2009-01-17
That was an awesome walkthrough, gneville, but it assumes 32bit.  Has anybody made this work on amd64?  I get this:

```
main.cpp:1: error: CPU you selected does not support x86-64 instruction set

```

when I "make"

Any thoughts??

---

### Post by gizmobay on 2009-01-17
Search for this in the Makefile

```
CFLAGS   = -pipe -march=pentiumpro -pthread -Wall -Wno-switch
```

I removed the -march=pentiumpro and it compiled under x86_64

---

### Post by larsolav on 2009-01-17
I am trying this too, but am hitting a snag. I first get the file
       wget [http://stashbox.org/352189/mythvodka.07.tar.gz](http://stashbox.org/352189/mythvodka.07.tar.gz)
But then when I do
      tar xzf mythvodka.07.tar.gz
I get this message:
> gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

I had tried searching, but can't find out how to resolve this....
Anyone have an idea?

---

### Post by gizmobay on 2009-01-17
I found wget doesn't work. Just open the link in a browser and then click on the file link to download.

---

### Post by tzoom84 on 2009-01-18
> **tzoom84 said:**
> I noticed around line 1009 of streamsui.cpp, there is the command:
```
argsStream += "/usr/local/bin/creatempeg.sh";
```

creatempeg.sh wasn't packed with the release, nor can I find it anywhere. Where can I find this? I believe this may be why *a certain feature* of MythVodka is not working for me right now

(BUMP) ... Still interested what this file is for, and where to get it.
Anyone? I'd like to use this feature.

---

### Post by gizmobay on 2009-01-18
There was some other packages on stashbox but none of them contained the creatempeg.sh file. This is probably why I can't get the NZB feeds to work.

---

### Post by larsolav on 2009-01-18
Thank you gizmobay,
downloading from the site worked! (Hey , did they remove the thank you button on the forum?)

I set up everything according to gneville's excellent instructions. But when I try to start it, it stalls at "Updating listings"at 40% for at least a couple of hours...
This version has the updated get_iplayer script. I don't quite understand the discussion in post # 44 and continuing. ( [http://ubuntuforums.org/showpost.php?p=6519640&postcount=44]("http://ubuntuforums.org/showpost.php?p=6519640&postcount=44") )
After a while a text box comes over the box with the progression bar, but the text scrolls so fast it looks like a white swooshy screen...
What do I do now?

---

### Post by gizmobay on 2009-01-18
I found it's best to do the grab by command line since you can see any issues in the terminal window. Here's how to do it.

Under MythVodka Setup change:

Hulu Grabber: /bin/cat /var/tmp/hulu.xml

Then generate the xml through the command line.

cd to /usr/local/bin then
#./gethulu.pl /var/tmp/hulu.xml
(this takes a long time)

Then once this is done start the frontend and go to MythVodka and then it'll import everything from the xml file. This takes a long time as well and you may end up with some seg faults so you have to keep any eye on it. If it seg faults the frontend, just restart and try again as sometimes it can't find urls so it faults. I had to do this a few times.

Once you do the whole process the initial time, it doesn't take as long the next go around. They suggest you set a cron job to do the xml generation but I do it manually since sometimes issues come up and if your family is using it they may not be as patience.

---

### Post by gneville on 2009-01-19
Thanks gizmobay

I have updated the wiki for 64-bit users.

I have also directly hosted mythvodka .07 on the wiki and my website.

---

### Post by tsx_5 on 2009-01-19
Is this plugin still working???  I get the following when I try it...

[http://releasegeo.hulu.com/content.select?pid=uxDEgMrjODijpGjk8oa6YcL0rsLe4TsM&mbr=true&format=smil](http://releasegeo.hulu.com/content.select?pid=uxDEgMrjODijpGjk8oa6YcL0rsLe4TsM&mbr=true&format=smil)
stream url
newUrl
rtmp://cp39465.hulu.com:1935/ondemand?_fcs_vhost=cp39465.hulu.com&auth=daEdScpaobVdHc6afdwdoc2akdWdncjcubS-bjDkh.-c0-0pKBvDu1Dzu&aifp=NS20070910&slist=content/43829/12/630/airforceone_240_2398_DST_8Mb_FLASH_700K_16x9_23_98__ePOrOJuI8UieuWB9BmGLsQ
[http://www.hulu.com/player.swf?_r=398181232380414345](http://www.hulu.com/player.swf?_r=398181232380414345)
content/43829/12/630/airforceone_240_2398_DST_8Mb_FLASH_700K_16x9_23_98__ePOrOJuI8UieuWB9BmGLsQ
rtmpdump --rtmp rtmp://cp39465.hulu.com:1935/ondemand?_fcs_vhost=cp39465.hulu.com\&auth=daEdScpaobVdHc6afdwdoc2akdWdncjcubS-bjDkh.-c0-0pKBvDu1Dzu\&aifp=NS20070910\&slist=content/43829/12/630/airforceone_240_2398_DST_8Mb_FLASH_700K_16x9_23_98__ePOrOJuI8UieuWB9BmGLsQ --swfUrl [http://www.hulu.com/player.swf?_r=398181232380414345](http://www.hulu.com/player.swf?_r=398181232380414345) --pageUrl [http://www.hulu.com/watch/46034](http://www.hulu.com/watch/46034) --app ondemand?_fcs_vhost=cp39465.hulu.com -o /var/tmp/iplayerdump.partial.mov --tcUrl rtmp://cp39465.hulu.com:1935/ondemand?_fcs_vhost=cp39465.hulu.com\&auth=daEdScpaobVdHc6afdwdoc2akdWdncjcubS-bjDkh.-c0-0pKBvDu1Dzu\&aifp=NS20070910\&slist=content/43829/12/630/airforceone_240_2398_DST_8Mb_FLASH_700K_16x9_23_98__ePOrOJuI8UieuWB9BmGLsQ
RTMP Dumper v1.3
(c) 2009 Andrej Stepanchuk, license: GPL

DEBUG: Setting buffer time to: 36000000ms
Connecting to rtmp://cp39465.hulu.com:1935/ondemand?_fcs_vhost=cp39465.hulu.com&auth=daEdScpaobVdHc6afdwdoc2akdWdncjcubS-bjDkh.-c0-0pKBvDu1Dzu&aifp=NS20070910&slist=content/43829/12/630/airforceone_240_2398_DST_8Mb_FLASH_700K_16x9_23_98__ePOrOJuI8UieuWB9BmGLsQ ...
DEBUG: Hostname: cp39465.hulu.com
DEBUG: Port: 1935
DEBUG: connected, hand shake:
DEBUG: handshaked
Connected...

Starting download at 0.000 KB
DEBUG: GetNextMediaPacket, received: invoke
DEBUG: Property: <Name:                  no-name., STRING:      _error>
DEBUG: Property: <Name:                  no-name., NUMBER:      1.00>
DEBUG: Property: NULL
DEBUG: Property: <Name:                  no-name., OBJECT>
DEBUG: Property: <Name:                     level, STRING:      error>
DEBUG: Property: <Name:                      code, STRING:      NetConnection.Connect.Rejected>
DEBUG: Property: <Name:               description, STRING:      [ AccessManager.Reject ] : Access denied!>
DEBUG: HandleInvoke, server invoking <_error>
ERROR: rtmp server sent error
DEBUG: GetNextMediaPacket, received: invoke
DEBUG: Property: <Name:                  no-name., STRING:      close>
DEBUG: Property: <Name:                  no-name., NUMBER:      0.00>
DEBUG: HandleInvoke, server invoking <close>
ERROR: rtmp server requested close
Closing connection... done!


Any idea?

---

### Post by bah1976 on 2009-01-19
Now I have a version mismatch I don't know how to solve.  If I try to install libmyth-dev (0.21.0 +fixes18207), it tells me:

```
  Depends: libmyth-0.21-0 (=0.21.0+fixes18207-0ubuntu4~hardy1) but 0.21.0+fixes18259-0ubuntu0+mythbuntu1 is to be installed

```

So if I try to force libmyth-0.21.0 to version 18207 it says it's going to remove pretty much every other myth component on the system.  Seems to me that isn't a good way to go...  Any way around the version mismatch?  I need libmyth-dev in order to compile this correctly.

Thanks...

---

### Post by gizmobay on 2009-01-19
I'm not sure why your packages are mismatched. The libmyth package revision I have matches the mythtv revision. Have you done an update in awhile. You could download the source rpm, unpack and then link to mythvodka as a last resort.

---

### Post by gizmobay on 2009-01-19
tsx_5, are you in the US? I thought hulu only worked for people in the US.

---

### Post by tsx_5 on 2009-01-19
Yes,

I sure am....

---

### Post by vv1gg1 on 2009-01-19
yes yes yes it works fine, its probably just technology rebelling against rubbish films.

heres the crazy creatempeg.sh script:

```
#!/bin/bash
export PATH=$PATH:/bin:/usr/bin:/usr/local/bin
export HOME=/root
source /etc/profile

mkdir /tmp/tmpnzb 2>/dev/null
cd /tmp/tmpnzb
MD5=`echo $1 | md5sum | awk '{print $1}'`
mkdir /tmp/tmpnzb/$MD5 2>/dev/null
cd /tmp/tmpnzb/$MD5
NZB=/tmp/tmpnzb/$MD5/tmpnzb.nzb

if [ -s $NZB ]
then
  echo "File exists, not downloading"
else
  wget -O $NZB $1
fi

rm -f /tmp/output.mpg 2>/dev/null

grep part01.rar $NZB
if [ $? = "0" ]
then
  FILTER="part"
  FIRSTFILTER="part01.rar"
  START=1
else
  FILTER="r"
  FIRSTFILTER="rar"
  START=0
fi

ls *$FIRSTFILTER* 1>/dev/null 2>/dev/null
if [ $? = "2" ]
then
  sleep 5
fi

# unrar p -inul `ls -tr *$FIRSTFILTER` *avi| mplayer -fs - 
 /opt/bin/unrar p -inul `ls -tr *$FIRSTFILTER*`| ffmpeg -re -i - -vcodec mpeg2video -qscale 1 -qmin 1 -acodec mp3 /tmp/output.mpg
# unrar p -inul `ls -tr *$FIRSTFILTER`| mencoder -o output.mpg -of mpeg -ovc lavc -oac mp3lame -lavcopts vcodec=mpeg2video:vbitrate=3200 -ofps 25 - &

# /opt/bin/unrar p -inul `ls -tr *$FIRSTFILTER*`| mencoder -o /tmp/output.mpg - 2>/dev/null 1>/dev/null

#sleep 4
#xterm -iconic -e /usr/local/bin/mythtv output.mpg
```


and a more recent getnzb.sh

```
#!/bin/bash

SERVER=$2
USERNAME=$3
PASSWORD=$4

mkdir /tmp/tmpnzb 2>/dev/null
cd /tmp/tmpnzb
MD5=`echo $1 | md5sum | awk '{print $1}'`
mkdir /tmp/tmpnzb/$MD5 2>/dev/null
cd /tmp/tmpnzb/$MD5
NZB=/tmp/tmpnzb/$MD5/tmpnzb.nzb

export DISPLAY=:0
pwd > /tmp/out.1
env > /tmp/out.2
bash -l -c "nznzb tmpnzb.nzb" >/tmp/out.noise
exit 0

if [ -s $NZB ]
then
  DONE="true"
else
  wget -O $NZB $1 1>/dev/null 2>/dev/null
fi

rm -f nzbperl* 1>/dev/null 2>/dev/null

grep part01.rar $NZB
if [ $? = "0" ]
then
  FILTER="part"
  FIRSTFILTER="part01.rar"
  START=1
else
  FILTER="r"
  FIRSTFILTER="rar"
  START=0
fi

LINES=`cat $NZB | grep \<file | grep $FILTER[0-9][0-9] | wc -l`;
LINES=`expr $LINES + 1`
I=$START;
O=0;
while [ $I -lt $LINES ]
do
    if [ $I -lt 10 ]
    then
      FILTERSTRING=$FILTER$O$I
    else
      FILTERSTRING=$FILTER$I
    fi
    nice -n10 xterm -iconic -e nzbperl.pl --server $SERVER --user $USERNAME --pw $PASSWORD --dthreadct 0 --filter $FILTERSTRING $NZB 1>/dev/null 2>/dev/null
    nice -n10 xterm -iconic -e nzbperl.pl --server $SERVER --user $USERNAME --pw $PASSWORD --dthreadct 0 --filter $FILTERSTRING $NZB 1>/dev/null 2>/dev/null
    nice -n10 xterm -iconic -e nzbperl.pl --server $SERVER --user $USERNAME --pw $PASSWORD --dthreadct 0 --filter $FILTERSTRING $NZB 1>/dev/null 2>/dev/null
    I=`expr $I + 1`;
done

```

The nzb getting stuff worked but im too damn cheap to get a usenet server that has completetion. Youll need nzbperl.pl, get that working before trying this. It used to use nzbget but they changed command params and things each version so i switched. In fact it looks like it also uses nznzb. Who knows, have a play.

Oh and a heads up, when I get back in a geeky mood for any period of time (and back in my parents basement, you repressed humourless moron, if I didnt take pleasure in the fact that people are being arsed to censor me id have stopped releasing this ages ago... whats that? youve got a family? you dont want to subject your childs fragile mind to "man love rules ok"? well the next version im going to hardcode it to play 2 girls 1 cup whilst buffering. Or even worse Ill make it randomly play a Rick Astley video instead of the content you wanted!) the new version will appear, it will seperate all content mining stuff and playing stuff from the GUI to make it easier to add new content and play new crazy streams.

Oh, in fact if anyone wants to create the XML with only good nzbs try using this checker script:

```
#!/usr/bin/perl -w

# use strict;
use News::NNTPClient;
use XML::DOM;
use XML::DOM;
use Data::Dumper;
use LWP::Simple;

my $newshost = '';
my $username = '';
my $password = '';
my $port     = '119';

# Connect to news server on port 119, debug level 1.
my $c = new News::NNTPClient($newshost, $port, 1);
unless ($c->ok()) {
  $c->quit();
  die $c->message();
}
$c->authinfo($username,$password);

#my $file = $ARGV[0];
my $file = get($ARGV[0]);
my $parser = new XML::DOM::Parser();

#my $doc = $parser->parsefile($file);
my $doc = $parser->parsestring($file);

$goodfiles = 0 ;
$badfiles = 0 ;

foreach my $groups ($doc->getElementsByTagName('group')){
  $group = $groups->getFirstChild()->getData();
}

$c->group($group);

foreach my $segments ($doc->getElementsByTagName('segment')){
  $segment = $segments->getFirstChild()->getData();
  $msgid = "<".$segment.">";
  $head = $c->head($msgid);
  if(length($head) > 0) {
    $goodfiles ++ ;
    print "+";
  } else { $badfiles ++ ; print "-"; } ;
}

$c->quit(); 

if($badfiles > 0){ die "There are $badfiles broken files."; }

```

God knows what hideous perl module dependancies that has, im sure a googling of error messages will get you what you need though.

---

### Post by gizmobay on 2009-01-19
I can't get the check file program to work as I keep getting these errors? Maybe I don't have the right command line syntax.

```
Use of uninitialized value in pattern match (m//) at /usr/lib/perl5/vendor_perl/5.8.8/LWP/Simple.pm line 133, <SOCK1> line 3.
Use of uninitialized value in subroutine entry at /usr/lib64/perl5/vendor_perl/5.8.8/x86_64-linux-thread-multi/XML/Parser/Expat.pm line 474, <SOCK1> line 3.

no element found at line 1, column 0, byte -1 at /usr/lib64/perl5/vendor_perl/5.8.8/x86_64-linux-thread-multi/XML/Parser.pm line 187

```

Also when I try to use NZB from the mythfrontend I get a log full of:

```
2009-01-19 15:12:19.887 How much completed..?: Executing '/usr/local/bin/getnzbdone.sh http://www.tvnzb.com/nzb/16222'
2009-01-19 15:12:19.970 Buffer Filled: 116243
2009-01-19 15:12:19.970 How much completed..?: Executing '/usr/local/bin/getnzbdone.sh http://www.tvnzb.com/nzb/16222'
2009-01-19 15:12:20.051 Buffer Filled: 116243

```

---

### Post by briangig on 2009-01-19
any ideas on why revision3 would disappear from the list?

---

### Post by larsolav on 2009-01-19
Thanks again gizmobay for your reply earlier! Tha got me passed the 40%!
I can now enter the world og MythVodka, but alas not play anything. I am in the US and Hulu (and the other streams) does not play. I first got the  beautifulsoup message, so i Installed it (sudo apt-get install python-beautifulsoup). Stll doesn't work... When in terminal window I try one random Hulu selection:
```
/usr/local/bin/hulu http://www.hulu.com/watch/49352 /var/tmp/iplayerdump.partial.mov
```
I get:
> [http://releasegeo.hulu.com/content.select?pid=x6iDJjW1YeKqAvR_Udkeky_Fgm7_JIR3&mbr=true&format=smil](http://releasegeo.hulu.com/content.select?pid=x6iDJjW1YeKqAvR_Udkeky_Fgm7_JIR3&mbr=true&format=smil)
stream url
rtmpdump --rtmp rtmp://cp39465.hulu.com:1935/ondemand?_fcs_vhost=cp39465.hulu.com\&auth=daEbKdJa1cgaNdLaabOcSc4bwa2dcdkaEd3-bjDshs-8-2qKBuEtYJAt\&aifp=NS20070910\&slist=content/41847/13/217/HuluTranscode_56037_52247_FLASH_700K_16x9_23_976__2QS7u-Vs3EeP0OllGdKYsg --swfUrl [http://www.hulu.com/player.swf?_r=235131232413138427](http://www.hulu.com/player.swf?_r=235131232413138427) --pageUrl [http://www.hulu.com/watch/49352](http://www.hulu.com/watch/49352) --app ondemand?_fcs_vhost=cp39465.hulu.com -o /var/tmp/iplayerdump.partial.mov --tcUrl rtmp://cp39465.hulu.com:1935/ondemand?_fcs_vhost=cp39465.hulu.com\&auth=daEbKdJa1cgaNdLaabOcSc4bwa2dcdkaEd3-bjDshs-8-2qKBuEtYJAt\&aifp=NS20070910\&slist=content/41847/13/217/HuluTranscode_56037_52247_FLASH_700K_16x9_23_976__2QS7u-Vs3EeP0OllGdKYsg
sh: rtmpdump: not found
How do I get this rtmpdump?

Thanks!

---

### Post by gizmobay on 2009-01-19
Download the rtmpdump tar file and untar. Install boost and boost-devel. Navigate to the rtmpdump directory then do make. It'll create a bin file called rtmpdump. Take this file and move it to your /usr/local/bin directory and then you're done.

---

### Post by tgm4883 on 2009-01-20
For anyone that wants a precompiled version, i've got one here 

[https://edge.launchpad.net/~tgm4883/+archive/ppa](https://edge.launchpad.net/~tgm4883/+archive/ppa)

It's packaged for Intrepid, I need to repush the hardy build, which i'm going to do tomarrow.

---

### Post by larsolav on 2009-01-20
Thanks yet again gizmobay!

I'll have to give this a try tonight when I get home.
Also, I guess I should have looked more carefully at the [MythStreams Wiki]("http://www.mythtv.org/wiki/MythStreams") where it says to get rtmpdump...

Gneville, maybe you should include the trmpdump getting step in your excellent how-to guide?

Thanks again!

---

### Post by larsolav on 2009-01-20
Me again!
Okidokili, I did the following:
```
wget http://garr.dl.sourceforge.net/sourceforge/rtmpdump/rtmpdump-v1.2a.tar.gz
tar xzf rtmpdump-v1.2a.tar.gz
cd rtmpdump
make
```

When I do "make" in the ~/rtmpdump directory I get this error:

> larsolav@MythBox1:~/rtmpdump$ make
g++ -Wall rtmp.cpp log.cpp AMFObject.cpp rtmppacket.cpp rtmpdump.cpp -o rtmpdump -lboost_regex
rtmp.cpp:30:27: error: boost/regex.hpp: No such file or directory
rtmp.cpp: In member function ‘bool RTMP_LIB::CRTMP::Connect(char*, char*, char*, char*, char*, char*, char*, double)’:
rtmp.cpp:80: error: ‘boost’ has not been declared
rtmp.cpp:80: error: expected `;' before ‘re’
rtmp.cpp:82: error: ‘boost’ has not been declared
rtmp.cpp:82: error: ‘re’ was not declared in this scope
rtmp.cpp:97: error: ‘boost’ has not been declared
rtmp.cpp:97: error: expected `;' before ‘matches’
rtmp.cpp:99: error: ‘boost’ has not been declared
rtmp.cpp:99: error: expected `;' before ‘re1’
rtmp.cpp:100: error: ‘boost’ has not been declared
rtmp.cpp:100: error: ‘matches’ was not declared in this scope
rtmp.cpp:100: error: ‘re1’ was not declared in this scope
rtmp.cpp:109: error: ‘matches’ was not declared in this scope
rtmp.cpp:113: error: ‘matches’ was not declared in this scope
make: *** [rtmpdump] Error 1

What is going on here?
I really want this to work....:o

---

### Post by gizmobay on 2009-01-20
> **gizmobay said:**
> Download the rtmpdump tar file and untar. **_[SIZE="2"]*Install boost and boost-devel*[/SIZE]_**. Navigate to the rtmpdump directory then do make. It'll create a bin file called rtmpdump. Take this file and move it to your /usr/local/bin directory and then you're done.

See quote bold, underline, italics

---

### Post by tgm4883 on 2009-01-21
This plugin doesn't play well with multiple frontend setups.  The initial startup on each machine is extremely long, even though the data that it imports is apparently in the db, and i'm using the same XML file between systems.

---

### Post by gneville on 2009-01-21
gizmobay thats for the instructions on rtmpdump.

larsolav, I have updated my Wiki page to include instructions on this. 

Cheers

---

### Post by jdeslip on 2009-01-21
Did anyone try tgm4883's package?

---

### Post by bah1976 on 2009-01-21
I'm using tgm4883's package on an amd64 Hardy system.  It installed perfectly, but I'm still working on getting it all to work.  Issues that I'm working through:
[LIST]
[*]I'm using a custom theme, so I had to manually add the buttons to it (no big deal).
[*]My apache install is https with a self-signed cert only, with user/password authentication so I had to edit the hulu-scan.py with appropriate settings.  the second to last line now looks like this:```
os.system("wget -q --no-check-certificate https://mythwebuser:mythwebpassword@"+BACKENDIP+"/hulu.xml -O /tmp/hulu.xml")

```
[*]the hulu-xml-generator isn't working for me (yet).  I ran the gethulu.pl manually, then the update from inside the plugin worked. (Press M in the plugin to get the update option)
[/LIST] 

The initial update of the hulu data took over an hour with a couple frontend crashes, as experienced by others.  Once that was done, subsequent "Update Streams" takes about 5 minutes to parse through the hulu.xml and make sure there's no missing programs data.  In a day or so I'll generate a new hulu.xml and see how long an update takes - I'd assume about the same.

tgm4883 - can code from inside a menubutton be added to your hulu-scan.py or hulu-xml-generator?  That's where the database update appears to be.  If that could be cron'd from the backend, then frontends wouldn't have to update at all and could just read the database.  But I don't know how to do that...

Also - my cron'd hulu-xml-generator does not run and I can't run the commands in there manually.  I changed it a bit and now looks like this:
```
/usr/bin/gethulu.pl /tmp/hulu.xml
mv /tmp/hulu.xml /var/www

```
(I took out the "su mythtv -c") and it now runs from the command line.  I'll wait for the daily job to run tomorrow to confirm this works.  I'd love to be able to port the menubutton code into this script - I'm not sure I'll be able to...

---

### Post by jdeslip on 2009-01-21
Hey Bah,

I am a bit confused but what you are saying.  Is your grabber path set to be a command that does '/bin/cat /var/tmp/hulu.xml' as the mythvodka wiki says?  In which case are you still getting the 5 minute wait?  I thought it would be instantaneous in this case...

---

### Post by bah1976 on 2009-01-21
My Hulu grabber is /usr/bin/hulu-scan.py which comes (I assume) from tgm4883's package.  The contents of that file are:
```
#!/usr/bin/python

import os
import string
import re

if os.path.isfile('/etc/mythtv/mysql.txt'):
  fi = open('/etc/mythtv/mysql.txt')
  for line in fi:
    if re.compile("^DBHostName").search(line):
      text=string.split(string.split(line,"=")[1],'\n')[0]
      BACKENDIP = text
fi.close()

os.system("wget -q --no-check-certificate https://mythwebuser:mythwebpassword@"+BACKENDIP+"/hulu.xml -O /tmp/hulu.xml")
os.system("/bin/cat /tmp/hulu.xml")

```

You'll notice the last line does what you reference, this is just a round-about way to use a hulu.xml that exists only on the backend of a multi-frontend setup.  If you've only got one, then the simple "/bin/cat /tmp/hulu.xml" should work.  The question I haven't figured all the way out is where the hulu.xml comes from if you don't generate it manually.  That's what the hulu-xml-generator is supposed to do, but I don't think it was part of the original mythvodka build.  I'm not an expert, i just poke around and get things to work sometimes... :)  The instantaneous bit is the plugin reading the database.  If you just browse the hulu menus, it's instant.  If you press M and Update Streams, that's what takes 5 minutes to parse the XML and make sure the database is current.

---

### Post by gizmobay on 2009-01-21
I use the gethulu.pl file to generate the xml file. I would guess if you don't have the bin/cat command as the grabber the gethulu.pl would create a temp file and generate this on the fly and then import everything into the database. This would probably take awhile since the grabber checks the xml file each time and then from there it pulls everything into the db which does take about 5 minutes.

From what I've seen by using mythvodka, is that it automatically updates the database once a day and this occurs once you go to view the streams. I'm not sure if it's checking the date of the file or just doing it.

I've also noticed a few bad urls for example the three stooges shows King of the Hill thumbnails and stream titles.

---

### Post by bah1976 on 2009-01-21
Correction - running my modified cron job does not work, as the normal user doesn't have access to /var/www - probably why tgm4883 had su in there.  Mine wasn't working that way - I'll have to investigate more...

---

### Post by tgm4883 on 2009-01-21
> **bah1976 said:**
> Correction - running my modified cron job does not work, as the normal user doesn't have access to /var/www - probably why tgm4883 had su in there.  Mine wasn't working that way - I'll have to investigate more...

Yea it didn't work well here either, i'm debugging it.  I think it might have something to do with the mv command and maybe a cp is in order.  It might also just be a permission issue, and may be why mythvodka is using /var/tmp/ by default.  I'll have to change it to that to see if it works.

The script I built myself, then just patched the source to point to it instead.  

I'd like to get the updating of the db into the cron job as well, but it needs further investigation.  I've noticed that in /var/tmp/mythvod/ there is a file for every show, so I need to figure out what that is for first and if I can scrap that altogether or if it is necessary to the operation of the plugin.

---

### Post by gizmobay on 2009-01-21
> **briangig said:**
> any ideas on why revision3 would disappear from the list?
I just lost it too.

---

### Post by tgm4883 on 2009-01-21
> **gizmobay said:**
> I just lost it too.

It use to grab it from [http://www.bewhere.co.uk/streams.xml](http://www.bewhere.co.uk/streams.xml) but if you go to that link, you will see nothing.  Probably why it has disappeared.

---

### Post by gizmobay on 2009-01-21
> **tgm4883 said:**
> It use to grab it from [http://www.bewhere.co.uk/streams.xml](http://www.bewhere.co.uk/streams.xml) but if you go to that link, you will see nothing.  Probably why it has disappeared.
Ah, I see. The url must of timed out so it removed them. I just did it again and they were re-added.

---

### Post by jdeslip on 2009-01-22
Ok.  So I got it more or less working with tgm4883s deb.  I changed the grabber to simply be the "bin/cat /tmp/hulu.xml" and the cron job to just create this file and not move anything.

I have noticed the following problems:

*It doesn't really look good in any of my themes...  Can I fix that somehow?  I currently use MePo-wide or Blootube-wide.

*It seems that if two TV shows have the same episode name, hulu gets confused and both menu items cause the first video to play.  For example, the most recent episode of The Office called "The Duel" plays some other TV show's episode called "The Duel."  Same is true with the Arrested Developments "Pilot" episode.  

*Clicking enter on the show name should take you to the list of episodes for the show and not just play the latest episode.  (But this is really minor).

---

### Post by jdeslip on 2009-01-22
Does anyone know how to get in touch with the developer?  I don't see his name listed anywhere.  I'd like to send some comments and patches.

---

### Post by tgm4883 on 2009-01-22
I think i've fixed the cron job in my package.  I've pushed the update to my ppa, so as soon as it builds you should be able to apt-get update and apt-get upgrade to it.  

> **jdeslip said:**
> Does anyone know how to get in touch with the developer?  I don't see his name listed anywhere.  I'd like to send some comments and patches.

The author didn't list anything on the page or in the package, but it is vv1gg1 on this forum (he's posted in this thread a few times).  There is no email listed, but you can either PM him or post the changes here and he will probably see them.

---

### Post by jdeslip on 2009-01-22
Ok.  The main change I have made so far that solves the problem with two tv shows having episodes of the same name is to change the two lines in gethulu.pl that look like this:

      print MYTHMENU "<Name>$eptitle</Name>\n";

to

      print MYTHMENU "<Name>$title-$eptitle</Name>\n";

It takes up a bit more room to write the title.  But, it is worth it in my opinion to have all the episodes work.

---

### Post by tgm4883 on 2009-01-22
> **jdeslip said:**
> Ok.  The main change I have made so far that solves the problem with two tv shows having episodes of the same name is to change the two lines in gethulu.pl that look like this:

      print MYTHMENU "<Name>$eptitle</Name>\n";

to

      print MYTHMENU "<Name>$title-$eptitle</Name>\n";

It takes up a bit more room to write the title.  But, it is worth it in my opinion to have all the episodes work.

Makes sense to me, patch added and set to my PPA.

---

### Post by samtay on 2009-01-22
Hey everyone,

I have seen this post ([http://www.gossamer-threads.com/lists/mythtv/users/367146](http://www.gossamer-threads.com/lists/mythtv/users/367146)). It contains a modified version of MythVODKA with "modules" to fill the database in a cron job.

---

### Post by tgm4883 on 2009-01-22
> **samtay said:**
> Hey everyone,

I have seen this post ([http://www.gossamer-threads.com/lists/mythtv/users/367146](http://www.gossamer-threads.com/lists/mythtv/users/367146)). It contains a modified version of MythVODKA with "modules" to fill the database in a cron job.

Very interesting.  I hadn't seen that.  I'll take a look.

---

### Post by jdeslip on 2009-01-22
Hey TGM4883 - Actually, I think the change I sugggested makes sense only in the second occurence of <name>$eptitle...  because the first refers to Hulu Movies.  

Also, can you change "Nascar Sucks / Hillary For President / Man Love Rules Ok" - To - "Buffering" or something more appropriate for guests ;)

---

### Post by samtay on 2009-01-22
Does any one know of a way to sort by category? I was looking at modifying the UI but I'm not much of a QT coder I know some C++, I just can't find any in-depth plugin development for MythTV. Does anyone know of one?

---

### Post by tgm4883 on 2009-01-22
> **jdeslip said:**
> Hey TGM4883 - Actually, I think the change I sugggested makes sense only in the second occurence of <name>$eptitle...  because the first refers to Hulu Movies.  

Also, can you change "Nascar Sucks / Hillary For President / Man Love Rules Ok" - To - "Buffering" or something more appropriate for guests ;)

Yea you are right, that makes more sense.  Fixed and pushed to PPA.

I also fixed all the quotes, I did my best to change all of them to something meaningful, let me know if I missed any or if there are better alternatives.

---

### Post by jdeslip on 2009-01-23
thanks tgm4883 - works great

---

### Post by Dubstar_04 on 2009-01-24
Does the iplayer stream work for anyone?

I have had to alter the mythvodka plugin and recompile to get it to work.

---

### Post by scary_jeff on 2009-01-24
> **Dubstar_04 said:**
> Does the iplayer stream work for anyone?

I have had to alter the mythvodka plugin and recompile to get it to work.

tgm4883's package installed properly for me, but I am unable to watch any of the BBC streams listed. Also, I only have liveTV streams listed - should I have the same selection that the iPlayer website has, or am I misunderstanding what this plugin is for?

---

### Post by Dubstar_04 on 2009-01-24
I have been watching iPlayer all morning!!!

Download and unzip the attachment and extract the binary to /usr/lib/mythtv/plugins

this works most of the time for me, although sometimes it does fail to play the first time.

Note: This will only work if you install tgm4883's package first. I would also advise making a back up of the existing libmythvodka.so first or keeping hold of tgm4883's package to write over this if it doesn't work for you.

please let me know if it works for you. I have changed some of the obscene language but i don't use hula so i've not changed that!

Regards,

Dubstar_04

---

### Post by tgm4883 on 2009-01-24
And I don't live in the UK, so I can't test BBC.  If you start mythfrontend from the terminal and then try to start mythvodka and play something from the BBC, there should be an error message printed to the terminal.  That would be very valuable.

---

### Post by Dubstar_04 on 2009-01-24
the only way i could get it to work was to comment the rtmp out of the source streamui.cpp line 802. it now works ok for me. 

There needs to be a little validation adding really to check if the program starts downloading and to control the % in the pop up. 

Some times the videos play fine but if i try the seconds later they won't play and some times it takes 2 or 3 attempts to get a video to play but on the whole its ok for now and saves switching to xbmc to watch iplayer!!

I am thinking of branching this off and making some mods to the source for my own use. if it is successful i will post here.

---

### Post by tgm4883 on 2009-01-24
Please, I'm asking of the original developer, the first guy who split this into modules, and any future people that split this into modules, It would help a lot if there was some sort of revision control in place that was public that we could check out up to date version of this plugin.  This would greatly help the development process and would allow patches to be summited back which would then be available with a quick update.  IMHO, it also makes everything much cleaner.  Might I suggest launchpad and bzr or sourceforge and svn.

Some documentation would be good too, but i'll suffice with some revision control.

---

### Post by tsx_5 on 2009-01-24
Patience,

[http://code.google.com/p/mythvodka/](http://code.google.com/p/mythvodka/) ....

Nothing there yet, however, work is afoot.

---

### Post by tgm4883 on 2009-01-24
> **tsx_5 said:**
> Patience,

[http://code.google.com/p/mythvodka/](http://code.google.com/p/mythvodka/) ....

Nothing there yet, however, work is afoot.

I'm hoping work is afoot, but it's been 3 weeks since that project has been registered, so I won't hold my breath

---

### Post by nrune on 2009-01-24
I have installed mythvodka to a remote frontend, I have compliled it and installed via deb and still running into the same error after doing some of importing the hulu.xml.  Here is the log. 

```
2009-01-22 17:54:26.788 Stream Data Has Expired. Refreshing.
2009-01-22 17:54:27.035 MythVodka Data Grabber: Executing '/usr/bin/curl -s -m 30 /var/tmp/hulu.xml'
2009-01-22 17:54:27.129 Grabber Finished. Processing Data.
2009-01-22 17:54:27.130 Error parsing data from grabber: Error: unexpected end of file Location Line: 1 Column 1

```

Any ideas?

---

### Post by tgm4883 on 2009-01-24
> **nrune said:**
> I have installed mythvodka to a remote frontend, I have compliled it and installed via deb and still running into the same error after doing some of importing the hulu.xml.  Here is the log. 

```
2009-01-22 17:54:26.788 Stream Data Has Expired. Refreshing.
2009-01-22 17:54:27.035 MythVodka Data Grabber: Executing '/usr/bin/curl -s -m 30 /var/tmp/hulu.xml'
2009-01-22 17:54:27.129 Grabber Finished. Processing Data.
2009-01-22 17:54:27.130 Error parsing data from grabber: Error: unexpected end of file Location Line: 1 Column 1

```

Any ideas?

looks like your hulu file didn't complete getting made.  You will have to make it again.

---

### Post by scary_jeff on 2009-01-24
> **tgm4883 said:**
> And I don't live in the UK, so I can't test BBC.  If you start mythfrontend from the terminal and then try to start mythvodka and play something from the BBC, there should be an error message printed to the terminal.  That would be very valuable.

Here's the output if I start mythfrontend, go to media > mythvodka, and tray and start 'BBC One'. Before applying Dubstar_04's version, I only got the (out of focus) "Sorry old bean, this file isn't available" message. Now I get a progress bar "Buffering BBC iPlayer Content", followed by the same message. The output below is using Dubstar_04's build.

```
2009-01-25 01:06:28.291 Using runtime prefix = /usr
2009-01-25 01:06:28.476 XScreenSaver support enabled
2009-01-25 01:06:28.477 DPMS is active.
2009-01-25 01:06:28.477 Empty LocalHostName.
2009-01-25 01:06:28.477 Using localhost value of scaz
2009-01-25 01:06:28.487 New DB connection, total: 1
2009-01-25 01:06:28.494 Connected to database 'mythconverg' at host: 192.168.1.31
2009-01-25 01:06:28.495 Closing DB connection named 'DBManager0'
2009-01-25 01:06:28.497 Primary screen 0.
2009-01-25 01:06:28.498 Connected to database 'mythconverg' at host: 192.168.1.31
2009-01-25 01:06:28.499 Using screen 0, 720x540 at 0,0
2009-01-25 01:06:28.519 New DB connection, total: 2
2009-01-25 01:06:28.520 Connected to database 'mythconverg' at host: 192.168.1.31
2009-01-25 01:06:28.522 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-01-25 01:06:28.523 Enabled verbose msgs:  important general
2009-01-25 01:06:28.898 No theme dir: /home/scaz/.mythtv/themes/ProjectGrayhem-wide
2009-01-25 01:06:28.899 Primary screen 0.
2009-01-25 01:06:28.899 Using screen 0, 720x540 at 0,0
2009-01-25 01:06:28.900 No theme dir: /home/scaz/.mythtv/themes/ProjectGrayhem-wide
2009-01-25 01:06:28.900 Switching to wide mode (ProjectGrayhem-wide)
2009-01-25 01:06:28.916 Using the Qt painter
2009-01-25 01:06:28.917 JoystickMenuClient Error: Joystick disabled - Failed to read /home/scaz/.mythtv/joystickmenurc
2009-01-25 01:06:28.918 lirc init success using configuration file: /home/scaz/.mythtv/lircrc
2009-01-25 01:06:29.419 Specified base font 'medium' does not exist for font clock
2009-01-25 01:06:29.419 Specified base font 'medium' does not exist for font small
2009-01-25 01:06:29.419 Specified base font 'medium' does not exist for font medium
2009-01-25 01:06:29.420 Specified base font 'medium' does not exist for font large
2009-01-25 01:06:29.420 Loading from: /usr/share/mythtv/themes/ProjectGrayhem-wide/base.xml
2009-01-25 01:06:29.458 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-25 01:06:29.490 Registering Internal as a media playback plugin.
2009-01-25 01:06:29.555 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-01-25 01:06:29.592 No theme dir: /home/scaz/.mythtv/themes/ProjectGrayhem-wide
2009-01-25 01:06:34.450 XMLParse::LoadTheme using /usr/share/mythtv/themes/default-wide/streams-ui.xml
2009-01-25 01:06:34.539 New DB connection, total: 3
2009-01-25 01:06:34.539 Connected to database 'mythconverg' at host: 192.168.1.31
2009-01-25 01:06:34.541 New DB connection, total: 4
2009-01-25 01:06:34.541 Connected to database 'mythconverg' at host: 192.168.1.31
2009-01-25 01:06:34.543 Rows: 14
2009-01-25 01:06:35.478 Rows: 14
2009-01-25 01:06:35.500 Rows: 2
2009-01-25 01:06:35.505 UIImageType::LoadImage() - Cannot find image: /var/tmp/mythvod/http://www.tvnzb.com/tvnzb_new.rss
2009-01-25 01:06:35.506 Rows: 14
2009-01-25 01:06:35.525 Rows: 0
2009-01-25 01:06:35.531 Rows: 0
2009-01-25 01:06:36.248 Rows: 14
2009-01-25 01:06:36.767 Rows: 14
2009-01-25 01:06:37.418 UIImageType::LoadImage() - Cannot find image: /var/tmp/mythvod/BBC Alba
2009-01-25 01:06:38.087 UIImageType::LoadImage() - Cannot find image: /var/tmp/mythvod/BBC Four
2009-01-25 01:06:38.851 UIImageType::LoadImage() - Cannot find image: /var/tmp/mythvod/BBC News
2009-01-25 01:06:39.144 UIImageType::LoadImage() - Cannot find image: /var/tmp/mythvod/BBC News 24
2009-01-25 01:06:39.565 UIImageType::LoadImage() - Cannot find image: /var/tmp/mythvod/BBC One
2009-01-25 01:06:40.106 Running Command: /usr/bin/get_iplayer -f --force-download -o /var/tmp --file-prefix iplayerdump --get b00gvg6n.mov
2009-01-25 01:06:40.106 Buffer Required: 300000
2009-01-25 01:07:04.196 Running Command: /usr/bin/playiplayer.sh /usr/bin/curl /usr/bin/mencoder b00gvg6n.mov
2009-01-25 01:07:04.196 Buffer Required: 3000000
2009-01-25 01:07:05.923 Selection: File: b00gvg6n.mov
2009-01-25 01:07:15.412 Connecting to backend server: 192.168.1.31:6543 (try 1 of 5)
2009-01-25 01:07:15.413 Using protocol version 40
2009-01-25 01:07:18.088 Deleting UPnP client...

```

---

### Post by tgm4883 on 2009-01-24
> **scary_jeff said:**
> Here's the output if I start mythfrontend, go to media > mythvodka, and tray and start 'BBC One'. Before applying Dubstar_04's version, I only got the (out of focus) "Sorry old bean, this file isn't available" message. Now I get a progress bar "Buffering BBC iPlayer Content", followed by the same message. The output below is using Dubstar_04's build.

```
2009-01-25 01:06:28.291 Using runtime prefix = /usr
2009-01-25 01:06:28.476 XScreenSaver support enabled
2009-01-25 01:06:28.477 DPMS is active.
2009-01-25 01:06:28.477 Empty LocalHostName.
2009-01-25 01:06:28.477 Using localhost value of scaz
2009-01-25 01:06:28.487 New DB connection, total: 1
2009-01-25 01:06:28.494 Connected to database 'mythconverg' at host: 192.168.1.31
2009-01-25 01:06:28.495 Closing DB connection named 'DBManager0'
2009-01-25 01:06:28.497 Primary screen 0.
2009-01-25 01:06:28.498 Connected to database 'mythconverg' at host: 192.168.1.31
2009-01-25 01:06:28.499 Using screen 0, 720x540 at 0,0
2009-01-25 01:06:28.519 New DB connection, total: 2
2009-01-25 01:06:28.520 Connected to database 'mythconverg' at host: 192.168.1.31
2009-01-25 01:06:28.522 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-01-25 01:06:28.523 Enabled verbose msgs:  important general
2009-01-25 01:06:28.898 No theme dir: /home/scaz/.mythtv/themes/ProjectGrayhem-wide
2009-01-25 01:06:28.899 Primary screen 0.
2009-01-25 01:06:28.899 Using screen 0, 720x540 at 0,0
2009-01-25 01:06:28.900 No theme dir: /home/scaz/.mythtv/themes/ProjectGrayhem-wide
2009-01-25 01:06:28.900 Switching to wide mode (ProjectGrayhem-wide)
2009-01-25 01:06:28.916 Using the Qt painter
2009-01-25 01:06:28.917 JoystickMenuClient Error: Joystick disabled - Failed to read /home/scaz/.mythtv/joystickmenurc
2009-01-25 01:06:28.918 lirc init success using configuration file: /home/scaz/.mythtv/lircrc
2009-01-25 01:06:29.419 Specified base font 'medium' does not exist for font clock
2009-01-25 01:06:29.419 Specified base font 'medium' does not exist for font small
2009-01-25 01:06:29.419 Specified base font 'medium' does not exist for font medium
2009-01-25 01:06:29.420 Specified base font 'medium' does not exist for font large
2009-01-25 01:06:29.420 Loading from: /usr/share/mythtv/themes/ProjectGrayhem-wide/base.xml
2009-01-25 01:06:29.458 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-25 01:06:29.490 Registering Internal as a media playback plugin.
2009-01-25 01:06:29.555 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-01-25 01:06:29.592 No theme dir: /home/scaz/.mythtv/themes/ProjectGrayhem-wide
2009-01-25 01:06:34.450 XMLParse::LoadTheme using /usr/share/mythtv/themes/default-wide/streams-ui.xml
2009-01-25 01:06:34.539 New DB connection, total: 3
2009-01-25 01:06:34.539 Connected to database 'mythconverg' at host: 192.168.1.31
2009-01-25 01:06:34.541 New DB connection, total: 4
2009-01-25 01:06:34.541 Connected to database 'mythconverg' at host: 192.168.1.31
2009-01-25 01:06:34.543 Rows: 14
2009-01-25 01:06:35.478 Rows: 14
2009-01-25 01:06:35.500 Rows: 2
2009-01-25 01:06:35.505 UIImageType::LoadImage() - Cannot find image: /var/tmp/mythvod/http://www.tvnzb.com/tvnzb_new.rss
2009-01-25 01:06:35.506 Rows: 14
2009-01-25 01:06:35.525 Rows: 0
2009-01-25 01:06:35.531 Rows: 0
2009-01-25 01:06:36.248 Rows: 14
2009-01-25 01:06:36.767 Rows: 14
2009-01-25 01:06:37.418 UIImageType::LoadImage() - Cannot find image: /var/tmp/mythvod/BBC Alba
2009-01-25 01:06:38.087 UIImageType::LoadImage() - Cannot find image: /var/tmp/mythvod/BBC Four
2009-01-25 01:06:38.851 UIImageType::LoadImage() - Cannot find image: /var/tmp/mythvod/BBC News
2009-01-25 01:06:39.144 UIImageType::LoadImage() - Cannot find image: /var/tmp/mythvod/BBC News 24
2009-01-25 01:06:39.565 UIImageType::LoadImage() - Cannot find image: /var/tmp/mythvod/BBC One
2009-01-25 01:06:40.106 Running Command: /usr/bin/get_iplayer -f --force-download -o /var/tmp --file-prefix iplayerdump --get b00gvg6n.mov
2009-01-25 01:06:40.106 Buffer Required: 300000
2009-01-25 01:07:04.196 Running Command: /usr/bin/playiplayer.sh /usr/bin/curl /usr/bin/mencoder b00gvg6n.mov
2009-01-25 01:07:04.196 Buffer Required: 3000000
2009-01-25 01:07:05.923 Selection: File: b00gvg6n.mov
2009-01-25 01:07:15.412 Connecting to backend server: 192.168.1.31:6543 (try 1 of 5)
2009-01-25 01:07:15.413 Using protocol version 40
2009-01-25 01:07:18.088 Deleting UPnP client...

```

Sorry, I should have specified, I need the output while it's broken.  Then I can debug and hopefully fix it.

---

### Post by scary_jeff on 2009-01-24
Maybe I misunderstood; I thought this is while it's broken. What I posted is everything from when I started mythfrontend, through to trying to watch BBC One using MythVodka, receving an error message, and then exiting mythfrontend.

---

### Post by tsx_5 on 2009-01-24
scary_jeff,

Do a "du -sh /var/tmp/*" and post the results -- my guess is b00gvg6n.mov
is of zero size....

You can also run "/usr/bin/get_iplayer -f --force-download -o /var/tmp --file-prefix iplayerdump --get b00gvg6n.mov" from a terminal and see what it outputs.


tgm4883: I happen to be the one trying to port this to qt4.... It looks like the original author is away from his system for another week.  Hopefully when he comes back I can jump on board.

---

### Post by scary_jeff on 2009-01-25
> **tsx_5 said:**
> scary_jeff,

Do a "du -sh /var/tmp/*" and post the results -- my guess is b00gvg6n.mov
is of zero size....

You can also run "/usr/bin/get_iplayer -f --force-download -o /var/tmp --file-prefix iplayerdump --get b00gvg6n.mov" from a terminal and see what it outputs.

```
scaz@scaz:~$ du -sh /var/tmp/*
1.1M	/var/tmp/mythvod
```

I tried running the command continually while trying to watch a stream. This produced the following (I left out outputs that were the same as the output before):

```
scaz@scaz:~$ du -sh /var/tmp/*
1.1M	/var/tmp/mythvod
scaz@scaz:~$ du -sh /var/tmp/*
0	/var/tmp/iplayerdump.partial.mov
1.1M	/var/tmp/mythvod
scaz@scaz:~$ du -sh /var/tmp/*
2.1M	/var/tmp/iplayerdump.partial.mov
1.1M	/var/tmp/mythvod
0	/var/tmp/stream.mpg
scaz@scaz:~$ du -sh /var/tmp/*
1.1M	/var/tmp/mythvod
```

The point at which the two new files disappear is the same time the "Sorry old bean..." message appears.

```
scaz@scaz:~$ /usr/bin/get_iplayer -f --force-download -o /var/tmp --file-prefix iplayerdump --get b00gvg6n.mov
INFO: Getting tv Index Feeds
.................
Added: 211:	Finley the Fire Engine - Finley Goofs Off, 'CBeebies', Children's,Entertainment & Comedy,Animation,TV, default
Added: 577:	The Koala Brothers: Series 1 - What Mitzi Wants, 'CBeebies', Children's,Entertainment & Comedy,Animation,TV, default
Matches:
22:	Antiques Roadshow: Series 31 - Wells, 'BBC One', Antiques,Factual,Sign Zone,TV, default,signed

INFO: 1 Matching Programmes
INFO: Attempting to Download: Antiques Roadshow: Series 31 - Wells
INFO: Getting version pids for programme b00gvg6n        
INFO: Checking existence of default version
INFO: File name prefix = iplayerdump                 
	16MB  1245kbps  11.8%, 00:21:46 remaining 
```

I didn't bother to let it complete. I was able to "scaz@scaz:/var/tmp$ mplayer iplayerdump.partial.mov" while the download was running, and watch the program... yay :D

I wonder if the problem is that in the mythvodka GUI, I can't select any individual program, as I am when using the command you asked me to run. The GUI only shows live TV streams. Maybe this fails because presumably the liveTV doesn't have a file size (since it goes on forever?). Just a guess. What would I have to put in --get *.mov in the command line in order to try and download a live feed?

Thanks for the help!

---

### Post by nrune on 2009-01-25
> looks like your hulu file didn't complete getting made. You will have to make it again.

Well I deleted /var/tmp/hulu.xml and reran the get_hulu script and it did generate the hulu.xml file. 

I am still having the same error 

```
2009-01-22 17:54:26.788 Stream Data Has Expired. Refreshing.
2009-01-22 17:54:27.035 MythVodka Data Grabber: Executing '/usr/bin/curl -s -m 30 /var/tmp/hulu.xml'
2009-01-22 17:54:27.129 Grabber Finished. Processing Data.
2009-01-22 17:54:27.130 Error parsing data from grabber: Error: unexpected end of file Location Line: 1 Column 1

```

Here are the first lines from the hulu.xml file

```
<MediaStreams>
<Feed><Name>21 Grams</Name><Provider>Hulu Movies</Provider><FeedImage>http://as$
<Stream>
<Name>21 Grams</Name>
<Url>http://www.hulu.com/watch/49352</Url>
```

Permissions error? 
Any help appreciated!

Not a permissons error.

---

### Post by tsx_5 on 2009-01-25
> **scary_jeff said:**
> Here's the output if I start mythfrontend, go to media > mythvodka, and tray and start 'BBC One'. Before applying Dubstar_04's version, I only got the (out of focus) "Sorry old bean, this file isn't available" message. Now I get a progress bar "Buffering BBC iPlayer Content", followed by the same message. The output below is using Dubstar_04's build.

2009-01-25 01:06:40.106 Buffer Required: 300000
2009-01-25 01:07:04.196 Running Command: /usr/bin/playiplayer.sh /usr/bin/curl /usr/bin/mencoder b00gvg6n.mov
2009-01-25 01:07:04.196 Buffer Required: 3000000
[/CODE]

Hmmm...  I'm not totally sure this is your problem (I haven't read through the thread to see how many people are successfully using the iplayer), however the code uses 2 different values for the buffer.  The smaller one is being used for the *timer* to wait for enough data to download -- the second is a check to see if enough data has been downloaded.  The 2nd is greater than the 1st.  If the program runs as expected, the player  will never work. (with a small exception, the loop that checks if enough data has been downloaded has a usleep -- if enough data is downloaded during that sleep period, things would work) 

Are you using the original download version (which would mean you compiled it)?  If so, that problem is easily addressed.  In mythvodka/mythvodka/streamsui.cpp line 818, add a 0 to the value set for bufferSizeMov.

---

### Post by tsx_5 on 2009-01-25
> 
Permissions error? 
Any help appreciated!

permission errors would be a good place to start -- give us the output from the following:

ls -al /var/tmp/*
du -sh /var/tmp/*

The error message you are getting is tracing back to something preventing the file from being read.

---

### Post by Dubstar_04 on 2009-01-25
scary_jeff, could you do something for me?

open your /var/tmp folder then open mythfrontend from the command line.

go to mythvodka and and select a recording then alt and tab to open the /var/tmp directory over your mythwindow

what you should see is a .partial.mov file appear and then a stream.mpg along side it. 

if this does not happen please could you tell me what you do see?

note: some times i have to attempt a couple of files before it will play but it does work eventually.

also make sure you have mencoder and curl installed in /usr/bin (you probably have but no harm in checking)

thanks,

Dubstar_04

---

### Post by slick666 on 2009-01-25
Hi,

I'm having a problem that I've seen earlier in the thread but I didn't see a good resolution. I'm using the ppa ([https://launchpad.net/~danser/+archive]("https://launchpad.net/~danser/+archive")) to install mythvodka and it is up to date.

The error I'm getting is:
> 
2009-01-25 11:50:08.368 MythVodka Data Grabber: Executing '/usr/bin/curl -s -m 30 [http://www.bewhere.co.uk/streams.xml](http://www.bewhere.co.uk/streams.xml)'
2009-01-25 11:50:08.906 Grabber Finished. Processing Data.
2009-01-25 11:50:08.950 Inserting prog: Stream Your Video and Music Anywhere!
2009-01-25 11:50:08.953 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-25 11:50:08.963 Server returned an error status code 0 for url: 
2009-01-25 11:50:08.965 Inserting prog: Three Portable USB Battery Packs You Can Build
2009-01-25 11:50:08.966 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-25 11:50:08.976 Server returned an error status code 0 for url: 
2009-01-25 11:50:08.978 Inserting prog: Cheap and Easy Hard Drive Upgrade
2009-01-25 11:50:08.979 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
...
2009-01-25 11:50:19.606 Server returned an error status code 0 for url: 
2009-01-25 11:50:19.610 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-25 11:50:19.620 Server returned an error status code 0 for url: 
2009-01-25 11:50:19.653 MythVodka Hulu Grabber: Executing '/usr/bin/hulu-scan.py'
2009-01-25 11:50:19.706 Grabber Finished. Processing Data.
2009-01-25 11:50:19.706 Error parsing data from grabber: Error: unexpected end of file Location Line: 1 Column 1


The front end works fine up until 40% and then crashes. It looks to me that there is as issue processing the info from the xml file. I'm a little stumped as to where to look. Has anyone else run into this problem?

---

### Post by scary_jeff on 2009-01-25
> **Dubstar_04 said:**
> scary_jeff, could you do something for me?

Thanks for helping me out Dubstar_04. I have verified curl and mencoder are present in /usr/bin, with the same permissions and owner as most of the other files in that folder.

I pretty much did what you suggested about monitoring /var/tmp for my post above #131.

I just realised I'm an idiot... I was pressing enter on the channel name, I didn't realise you had to go right to give a list of programs for that channel. Anyway, it doesn't seem to make any difference if I select a channel or a particular program, the result is the same. The two files you mentioned do appear, but as soon as the stream.mpg file appears, the "Sorry old bean..." message pops up, and both files disappear.

> **tsx_5 said:**
> Are you using the original download version (which would mean you compiled it)?  If so, that problem is easily addressed.  In mythvodka/mythvodka/streamsui.cpp line 818, add a 0 to the value set for bufferSizeMov.

Thanks tsx_5. I did originally try and build from source, but I gave up on that once tgm4883 produced a working package. I then replaced the libmythvodka.so with the one provided by Dubstar_04.

---

### Post by Dubstar_04 on 2009-01-25
scary_jeff,

I have attached a new mythvodka for you to try.

note this one will not build the list of hulu videos or nbzs in to the tree as i dont use either of them.

I really hope this works for you as it is working really well for me after recent changes i have made!!

let me know if the buffer progress bar works for you.

---

### Post by scary_jeff on 2009-01-25
Wow, thanks Dubstar_04! The buffering progress bar takes a while to jump to 30ish percent, then works smoothly up to 100%. The program then plays! Really an impressive feature to be able to run iPlayer all using the same controls, GUI etc as the rest of mythtv.
Onto the bad news. The program stops playing after a 1 or 2 minutes. There's no errors in the terminal output, or the frontend/backend logs. I thought perhaps my connection is too slow, but using the iPlayer website proved otherwise. Maybe BBC gives less bandwidth to you if you're not using their player?
I kept 'top' open while trying to watch, and mencoder only appears as a process using more than 0% of the CPU for a couple of seconds, at 99%... shouldn't this process be running the whole time I'm watching? Or at least at regular intervals as a new chunks of program are downloaded? I don't know if a couple of seconds is long enough for a c2d e2200 to transcode the ~1 minute of video I am able to watch.
Still, I'm really impressed with this plugin, can't wait to have it working properly.

---

### Post by Dubstar_04 on 2009-01-25
Wow thats fantastic news!!!

The problem with it cutting out should be easy to solve!!

First could you please try pausing it for 30 seconds and seeing if it adds 30 seconds to the time it will play?

what i think is happening is it reaches what it thinks is the end if the file and quits, so if you pause and it works you can simply make it buffer a bigger file. 

regards,

Dubstar_04

---

### Post by scary_jeff on 2009-01-25
Ok, I just tried that. I'm using 'BBC Two - Natural World - Polar Bears and Grizlies...' as the test program (I did try a couple of others to confirm the 'stops playing' thing).
If I do not pause, the video plays for 56 seconds, including a slight skip after 50 seconds. If I pause it as soon as it starts playing, for 30 seconds, the timings are the same. Interestingly, when I unpause, the time remaining says only 16 seconds (and is not incrementing), even though I am able to watch tripple this time. The prebuffering takes 44 seconds.
I tried Best of Top Gear, same prebuffering time, but slightly less run time, and the 'skip' also occurs slightly earlier (I didn't bother to get exact times for that).
Hope this info helps you! Thanks for sorting this out :D

---

### Post by tsx_5 on 2009-01-25
> **Dubstar_04 said:**
> scary_jeff,

I have attached a new mythvodka for you to try.

note this one will not build the list of hulu videos or nbzs in to the tree as i dont use either of them.

I really hope this works for you as it is working really well for me after recent changes i have made!!

let me know if the buffer progress bar works for you.

Hi,

Could I see your code? I can go ahead and add it into my work...

---

### Post by nrune on 2009-01-25
ls -al /var/tmp/*
-rw-r--r-- 1 nrune nrune 3703202 2009-01-24 22:52 /var/tmp/hulu.xml

kdecache-nrune
drwx------ 5 nrune nrune   4096 2008-12-03 05:45 http
-rw-r--r-- 1 nrune nrune 425022 2008-12-03 05:45 ksycoca
-rw-r--r-- 1 nrune nrune    686 2008-12-03 05:45 ksycocastamp

mythvod
lots and lots of 
-rw-r--r-- 1 nrune nrune   9277 2009-01-22 18:50 You've Got a Friend
-rw-r--r-- 1 nrune nrune  10555 2009-01-22 18:53 You Win Some, You Lose Some
-rw-r--r-- 1 nrune nrune  13723 2009-01-22 18:52 Zach Hickoff, Malia Manuel, Mitch Ropelato
-rw-r--r-- 1 nrune nrune  13641 2009-01-22 18:56 Zap! Victory is Always Mine!
-rw-r--r-- 1 nrune nrune  12897 2009-01-25 08:32 ZAP! (Zinfandel Advocates  Producers)
-rw-r--r-- 1 nrune nrune  11751 2009-01-22 18:46 Zen and the Art of Law Enforcement
-rw-r--r-- 1 nrune nrune  10065 2009-01-22 18:43 Zero
-rw-r--r-- 1 nrune nrune  12451 2009-01-22 18:44 Zip me Up

du -sh /var/tmp/*
3.6M	/var/tmp/hulu.xml
512K	/var/tmp/kdecache-nrune
110M	/var/tmp/mythvod

---

### Post by Dubstar_04 on 2009-01-25
I have attached my modified streamui.cpp file i havent deleted any code, the original is all commented out. 

scarey_jeff if you keep having problems try playing the files with mplayer. to do that go to your media settings in mythtv and change your default from 'Internal' to  'mplayer -fs -aspect 4:3 -zoom -quiet -vo xv %s' 

note: you can leave out the -aspect 4:3 if you are on 16:9

if that doesnt help then I will build you a custom plugin with a longer buffer.

cheers,

Dubstar_04

---

### Post by scary_jeff on 2009-01-25
Hi again Dubstar_04. I tried using mplayer - I know it worked because the remote control didn't do anything while the video was playing. Basically it's exactly the same.

The problem seems to be that although the flv grabber bit doesn't appear to have an issue in downloading the feed, mencoder only ever does anything with the part of the program buffered during the prebuffer stage, so the stream.mpg is never longer than the original buffer size. That doesn't explain the glitch a few seconds before the playback ends, so I don't have all that much faith in my logic. I'm not building from source and I don't have any debug output so this is all just a guess really.

I'll leave this until tomorrow after work now. Really appreciate all your help today, Dubstar_04. Cheers.

---

### Post by tgm4883 on 2009-01-25
> **slick666 said:**
> Hi,

I'm having a problem that I've seen earlier in the thread but I didn't see a good resolution. I'm using the ppa ([https://launchpad.net/~danser/+archive]("https://launchpad.net/~danser/+archive")) to install mythvodka and it is up to date.

The error I'm getting is:


The front end works fine up until 40% and then crashes. It looks to me that there is as issue processing the info from the xml file. I'm a little stumped as to where to look. Has anyone else run into this problem?

IIRC, thats because you don't have rtmpdump installed.  Don't use the danser PPA, as that is out of date.  Instead use [https://launchpad.net/~tgm4883/+archive](https://launchpad.net/~tgm4883/+archive)

---

### Post by Dubstar_04 on 2009-01-25
I have made a video to show how my mythvodka build plays in hope that we can all get to the same stage.

please note that this is a custom build with Hulu, NZBs, and most iplayer channels missing because i don't want them!

[http://uk.youtube.com/watch?v=hwLliA9LRjo](http://uk.youtube.com/watch?v=hwLliA9LRjo)

I apologize for it being low quality i will do a better one when I have made more progress. 

The next thing i want to look at is stopping the progress dialog flashing up when you swap between feeds as it make the plugin look cheap which it is not. 

I would also like to ask that everyone who enjoys using this plugin to acknowledge that vv1gg1 is the original author and all thanks should go to him as without his work we would not be using this plugin at all and I dont think its too much to ask that we all thank him for his work given the chance. 


kind regards,

Dubstar_04

---

### Post by slick666 on 2009-01-25
ok,

I switched the ppa then
> apt-get remove mythvodke
apt-get install mythvodka

I also checked and made sure that I had rtmpdump installed before and after switching the ppa I still have it installed and it's version is 1.3

> landon@MythBox:~$ rtmpdump --version
RTMP Dumper v1.3
(c) 2009 Andrej Stepanchuk, license: GPL


I'm still getting the same problem. Anyone got any ideas?

---

### Post by tgm4883 on 2009-01-25
> **slick666 said:**
> ok,

I switched the ppa then


I also checked and made sure that I had rtmpdump installed before and after switching the ppa I still have it installed and it's version is 1.3



I'm still getting the same problem. Anyone got any ideas?

Hmm, I just went back and reread your log.  How did you get hulu-scan.py if you weren't already running it from my ppa?

Anywho, you need to install hulu-xml-maker on your master backend and then either A) wait for your daily cron job to run, or B) if you don't feel like waiting, then run do ```
sudo /etc/cron.daily/hulu-xml-maker
``` and wait about an hour for the XML file to be generated.

---

### Post by slick666 on 2009-01-25
ok, got it installed and am running it now. Hopefully this will get me going. I'll let you know, thanks for your help.

---

### Post by iitywygms on 2009-01-26
is the ppa for 8.04.01 available yet?

---

### Post by tgm4883 on 2009-01-26
> **iitywygms said:**
> is the ppa for 8.04.01 available yet?

Hardy and Intrepid builds are available here
[https://edge.launchpad.net/~tgm4883/+archive/ppa](https://edge.launchpad.net/~tgm4883/+archive/ppa)

---

### Post by Dubstar_04 on 2009-01-26
Good evening guys.

I have attached a copy of mythvodka with yet more code commented out as this now removes the progress dialog when switching between feeds and it gives a more more solid and polished feel to mythvodka. 

My wish list:

- Search feature for iplayer (top priority) 
- Artwork for shows
- Ability to drill further into the iplayer eg series -> episodes (get_iplayer script mods)
- possibly a new layout as the current one uses a dated stucture (could be included in the QT4 port? see mythtube)

Does anyone else have any ideas to improve this plugin?

Also I read a few posts back that someone wanted to start tracking the development of mythvodka. We should definitely do this however i am worried about stepping on the original authors toes!!

the best place would be in trac but peoplw will have issues getting access to trac to post mods / patches!

regards,

Dubstar_04

---

### Post by nrune on 2009-01-26
Still having crashing issues...

When run from the command line...
```
709:	Wolverine & The X-Men - Overflow, 'CBBC', Children's,Entertainment & Comedy,Animation,TV, default
710:	Wolverine & The X-Men - Thieves' Gambit, 'CBBC', Children's,Entertainment & Comedy,Animation,TV, default

INFO: 7 Matching Programmes

2009-01-26 19:04:31.664 Grabber Finished. Processing Data.
2009-01-26 19:04:31.666 Error parsing data from grabber: Error: error occurred while parsing element Location Line: 1 Column 1

```

Help...

---

### Post by slick666 on 2009-01-26
still having the same problems here guys
 very similar to nrune (see previous posts). I'm rebuild my hulu.xml and trying again. Any input is welcome, still poking at it over here.

---

### Post by iitywygms on 2009-01-26
I am running into some issues.  It updates to 40% then crashes.  Here is a snipit of mythfrontend.log

2009-01-26 17:22:38.140 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-26 17:22:38.150 Server returned an error status code 0 for url: 
2009-01-26 17:22:38.155 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-26 17:22:38.165 Server returned an error status code 0 for url: 
2009-01-26 17:22:38.178 MythVodka Hulu Grabber: Executing '/usr/bin/hulu-scan.py'
2009-01-26 17:22:38.215 Grabber Finished. Processing Data.
2009-01-26 17:22:38.215 Error parsing data from grabber: Error: unexpected end of file Location Line: 1 Column 1

Any ideas?

---

### Post by tgm4883 on 2009-01-26
> **iitywygms said:**
> I am running into some issues.  It updates to 40% then crashes.  Here is a snipit of mythfrontend.log

2009-01-26 17:22:38.140 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-26 17:22:38.150 Server returned an error status code 0 for url: 
2009-01-26 17:22:38.155 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-26 17:22:38.165 Server returned an error status code 0 for url: 
2009-01-26 17:22:38.178 MythVodka Hulu Grabber: Executing '/usr/bin/hulu-scan.py'
2009-01-26 17:22:38.215 Grabber Finished. Processing Data.
2009-01-26 17:22:38.215 Error parsing data from grabber: Error: unexpected end of file Location Line: 1 Column 1

Any ideas?

You need to have hulu-xml-maker installed on your master backend.  Alternatively, you could generate the hulu.xml file locally, but on multi-system networks this is a waste.

After you install hulu-xml-maker, either wait for the daily cron jobs to run, or manually run "sudo /etc/cron.daily/hulu-xml-maker

---

### Post by iitywygms on 2009-01-26
dude, you are the best.  I remeber having other issues and you also helped me then.
This forum is a better place with you in it.
I will report after it is finished running if I have other issues.
Thanks

---

### Post by iitywygms on 2009-01-27
Okay, this is AWESOME!!!!!
Now, has anyone tried to get a remote control to work?  I assume I have to set up lircrc to control mplayer correct?

Thanks

---

### Post by tgm4883 on 2009-01-27
> **iitywygms said:**
> dude, you are the best.  I remeber having other issues and you also helped me then.
This forum is a better place with you in it.
I will report after it is finished running if I have other issues.
Thanks

/me blushes :oops:  Thanks, that was a nice thing to say.

---

### Post by tgm4883 on 2009-01-27
> **iitywygms said:**
> Okay, this is AWESOME!!!!!
Now, has anyone tried to get a remote control to work?  I assume I have to set up lircrc to control mplayer correct?

Thanks

yea you would have to set up lirc to control mplayer, although I haven't done much testing with the hulu stuff as it's streaming.  I think it might not work so well.

I just used MCC with my Windows MCE remote and it was configured OOB

---

### Post by iitywygms on 2009-01-27
> **tgm4883 said:**
> yea you would have to set up lirc to control mplayer, although I haven't done much testing with the hulu stuff as it's streaming.  I think it might not work so well.

I just used MCC with my Windows MCE remote and it was configured OOB

Actually, I think my remote does control mplayer.  When I play avi videos or music, I can pause, skip, ect.  
Problem I have is that I cannot exit once I start playing a show in mythvodka.  I have to ssh to my box and kill mplayer to get back to the frontend.
If I could just cleanly exit that would be enough for now.

and it was configured OOB <-- what does that mean??

---

### Post by Dubstar_04 on 2009-01-27
> **iitywygms said:**
> Actually, I think my remote does control mplayer.  When I play avi videos or music, I can pause, skip, ect.  
Problem I have is that I cannot exit once I start playing a show in mythvodka.  I have to ssh to my box and kill mplayer to get back to the frontend.
If I could just cleanly exit that would be enough for now.

and it was configured OOB <-- what does that mean??

if you go in to mythfrontend settings and change the default player from mplayer to Internal you shouldnt have any problems.

---

### Post by tgm4883 on 2009-01-27
> **iitywygms said:**
> Actually, I think my remote does control mplayer.  When I play avi videos or music, I can pause, skip, ect.  
Problem I have is that I cannot exit once I start playing a show in mythvodka.  I have to ssh to my box and kill mplayer to get back to the frontend.
If I could just cleanly exit that would be enough for now.

and it was configured OOB <-- what does that mean??

Out Of Box

I just hit the Stop button on my MCEUSB2 remote (I believe it's configured as Escape) and it exits the show.  One bug though, it will continue downloading the rest of the show until either A) it has downloaded the complete show, or B) you start streaming a new show

---

### Post by Dubstar_04 on 2009-01-27
tgm4883,

There is code in the iplayer script that halts the download and deletes the files from /var/tmp. 

I havent used hulu because im in the uk, but it should behave in the same way if not you could just reuse the iPlayer code to recieve the exit signal from the video player. 

I will have a look at the code when i get home and be more specific if you want?

Thanks,

Dan

---

### Post by nrune on 2009-01-27
Sorry I am still missing something somewhere. 

I ran hulu-xml-maker and I have hulu.xml in the /tmp/www/ dir on my master backend. Not sure what to put in place of the hulu grabber line, I just deleted it to see what would happen, and I got the same error. 

```
703:	Wolverine & The X-Men - Overflow, 'CBBC', Children's,Entertainment & Comedy,Animation,TV, default
704:	Wolverine & The X-Men - Thieves' Gambit, 'CBBC', Children's,Entertainment & Comedy,Animation,TV, default

INFO: 6 Matching Programmes

2009-01-27 11:48:49.893 Grabber Finished. Processing Data.
2009-01-27 11:48:49.895 Error parsing data from grabber: Error: error occurred while parsing element Location Line: 1 Column 1

```

So this error happens if there is a hulu grabber line filled in or not. 

Is it something to do with being in the US and it is grabbing BBC stuff? Is there a way to eliminate the bbc grabber just to see if that is the problem? 

I will try an mythvodka install on the master backend to see if that helps. 

Thanks

NEVER MIND it's working!

---

### Post by iitywygms on 2009-01-27
> **Dubstar_04 said:**
> if you go in to mythfrontend settings and change the default player from mplayer to Internal you shouldnt have any problems.

Are you talking about the file extension settings????  Or a different area?

If it is the extensions,

Which extension should I change to the default player?  I see VOB, mpeg, txt, and others.  Should I create a new extension, (flv) and make it use the default player, or internal?


Under file extensions.
In order to make my remote control hd rips in video player, I had to create a mkv extension and remove the internal option.  Perhaps I need to do this for mythvodka.

---

### Post by iitywygms on 2009-01-27
Today I came home from work to experiment with player settings.
I started mythvodka and is scanned to 40% and then gave me an error, I should have written it down but it had to do with permissions of hulu.xml check mythvodka settings.  So i changed permissions of hulu.xml.  They were originally, owner mythtv, group nogroup.  I changed them to group mythtv with read-write and others with read-write.
Now when I start mythvodka it crashes at 40%
Here is the last few lines of mythfrontend.log


edit exact error mentioned above.  "/usr/bin/hulu-scan.py: /tmp/hulu.xml: Permission denied

Check MythVodkaSettings


2009-01-27 16:44:15.749 Server returned an error status code 0 for url:
2009-01-27 16:44:15.759 Inserting prog: Nicholas Crane's Britannia: The Great Elizabethan Journey
2009-01-27 16:44:15.761 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-27 16:44:15.771 Server returned an error status code 0 for url:
2009-01-27 16:44:15.778 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-01-27 16:44:15.788 Server returned an error status code 0 for url:
2009-01-27 16:44:15.801 MythVodka Hulu Grabber: Executing '/usr/bin/hulu-scan.py'
2009-01-27 16:44:16.251 Grabber Finished. Processing Data.
2009-01-27 16:44:16.762 Error parsing data from grabber: Error: unexpected end of file Location Line: 19743 Column 1

Thanks

---

### Post by larsolav on 2009-01-27
For those of you who have this working, are you guys using SPDIF sound? I can't get any audio from for example Hulu... Funny thing is that I can hear stuff when I access Hulu from Firefox.
For a full description see [http://ubuntuforums.org/showthread.php?t=1051588]("http://ubuntuforums.org/showthread.php?t=1051588")

---

### Post by iitywygms on 2009-01-27
> **larsolav said:**
> For those of you who have this working, are you guys using SPDIF sound? I can't get any audio from for example Hulu... Funny thing is that I can hear stuff when I access Hulu from Firefox.
For a full description see [http://ubuntuforums.org/showthread.php?t=1051588]("http://ubuntuforums.org/showthread.php?t=1051588")

Yes, I am using spdif.  When mythvodka was working I had no sound problems.

aplay: version 1.0.15 by Jaroslav Kysela <perex@perex.cz>


**** List of PLAYBACK Hardware Devices ****

card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]

  Subdevices: 0/1

  Subdevice #0: subdevice #0

card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]

  Subdevices: 1/1

  Subdevice #0: subdevice #0


default:CARD=CMI8738

    C-Media CMI8738, C-Media PCI DAC/ADC

    Default Audio Device

front:CARD=CMI8738,DEV=0

    C-Media CMI8738, C-Media PCI DAC/ADC

    Front speakers

iec958:CARD=CMI8738,DEV=0

    C-Media CMI8738, C-Media PCI DAC/ADC

    IEC958 (S/PDIF) Digital Audio Output

null

    Discard all samples (playback) or generate zero samples (capture)

---

### Post by larsolav on 2009-01-27
Thanks for looking into this!
How about your  ./etc/asound.conf, do you have one?
Cheers!

---

### Post by iitywygms on 2009-01-27
I do not have that file listed.

---

### Post by iitywygms on 2009-01-28
I have some sort of permission issue
If I run
sudo /etc/cron.daily/hulu-xml-maker

When it finishes after about an hour, I get this

cp: cannot create regular file `/var/www/hulu.xml': Permission denied

Any ideas?

---

### Post by slick666 on 2009-01-28
what I did to get around it quickly was:
> chmod 777 /var/www/hulu.xml
it may not be the cleanest way of doing it but ti works.

---

### Post by tgm4883 on 2009-01-28
> **iitywygms said:**
> I have some sort of permission issue
If I run
sudo /etc/cron.daily/hulu-xml-maker

When it finishes after about an hour, I get this

cp: cannot create regular file `/var/www/hulu.xml': Permission denied

Any ideas?

Whats the output of "ls -l /var/w*"

---

### Post by iitywygms on 2009-01-28
I can tell you that last night when i looked at the www folder using thunar, the owner was root read write, group was mythtv read write, and everyone else was read write.  If I understand permissions correctly that should be okay.
To try something different,I changed the group to kevin (me) with read write.
Then I ran sudo /etc/cron.daily/hulu-xml-maker
That then finished without any errors.  So then I started mythvodka, it got to 40% and then crashed and kicked me out of the frontend.  I checked the mythfrontend.log and the last line was something along the lines of error parsing frame grabber.  I am at work now and can't be more specific.
I think I will remove everything and reinstall and try again unless someone wants me to try something else.
I am puzzled about the permission thing.  
What should the default permissions of www be?

---

### Post by tgm4883 on 2009-01-28
> **iitywygms said:**
> I can tell you that last night when i looked at the www folder using thunar, the owner was root read write, group was mythtv read write, and everyone else was read write.  If I understand permissions correctly that should be okay.
To try something different,I changed the group to kevin (me) with read write.
Then I ran sudo /etc/cron.daily/hulu-xml-maker
That then finished without any errors.  So then I started mythvodka, it got to 40% and then crashed and kicked me out of the frontend.  I checked the mythfrontend.log and the last line was something along the lines of error parsing frame grabber.  I am at work now and can't be more specific.
I think I will remove everything and reinstall and try again unless someone wants me to try something else.
I am puzzled about the permission thing.  
What should the default permissions of www be?

Mines 

```
drwxr-xr-x  2 root root  4096 2009-01-26 18:19 www

```

As odd as it might sound, if it's not saying anything about permission problems, do this.

Use the terminal to open up mythfrontend, then go into mythvodka.  Use alt-tab to go back to the terminal to watch the output.  If you are at 40% and it says it's importing shows then you should be fine.  With that being said, it might still crash the frontend.  We aren't sure why, but I think if it has to do a lot of importing it crashes.  If it does crash, you can go back into it and it will resume where it left off.  My first time running the program it crashed 4 or 5 times before I actually got into watching some shows.  The next day I ran the program, it updated relatively quickly and did not crash.

---

### Post by iitywygms on 2009-01-28
> **tgm4883 said:**
> Whats the output of "ls -l /var/w*"

kevin@mythtv:~$ ls -l /var/w*
total 1180
-rw-rw-rw- 1 root  kevin      21 2009-01-03 12:41 htpasswd
-rw-r--r-- 1 kevin kevin 1196032 2009-01-28 07:17 hulu.xml
-rw-r--r-- 1 root  kevin      45 2009-01-05 18:26 index.html
lrwxrwxrwx 1 root  root       25 2009-01-05 18:28 mythweb -> /usr/share/mythtv/mythweb

is this right??

---

### Post by tgm4883 on 2009-01-28
> **iitywygms said:**
> kevin@mythtv:~$ ls -l /var/w*
total 1180
-rw-rw-rw- 1 root  kevin      21 2009-01-03 12:41 htpasswd
-rw-r--r-- 1 kevin kevin 1196032 2009-01-28 07:17 hulu.xml
-rw-r--r-- 1 root  kevin      45 2009-01-05 18:26 index.html
lrwxrwxrwx 1 root  root       25 2009-01-05 18:28 mythweb -> /usr/share/mythtv/mythweb

is this right??

Looks right to me, I don't have the htpasswd in there though but if you are able to download the hulu.xml file from another system then that is alright.

If you are getting this error

```
 Error parsing data from grabber: Error: unexpected end of file Location Line: 19760 Column 1

```

Then that means the xml file is corrupt and probably needs to be regenerated.  I'm going to do some testing to see if I can make it auto-regenerate if it's broke.

---

### Post by iitywygms on 2009-01-28
> **tgm4883 said:**
> Looks right to me, I don't have the htpasswd in there though but if you are able to download the hulu.xml file from another system then that is alright.

If you are getting this error

```
 Error parsing data from grabber: Error: unexpected end of file Location Line: 19760 Column 1

```

Then that means the xml file is corrupt and probably needs to be regenerated.  I'm going to do some testing to see if I can make it auto-regenerate if it's broke.

to regenerate I should run this again correct?

sudo /etc/cron.daily/hulu-xml-maker

---

### Post by tgm4883 on 2009-01-28
> **iitywygms said:**
> to regenerate I should run this again correct?

sudo /etc/cron.daily/hulu-xml-maker

Correct.

---

### Post by tgm4883 on 2009-01-28
In an attempt to detect invalid XML files and regenerate automatically, I've pushed another update to hulu-xml-maker.

---

### Post by tgm4883 on 2009-01-28
> **tgm4883 said:**
> In an attempt to detect invalid XML files and regenerate automatically, I've pushed another update to hulu-xml-maker.

I've pushed another update as I realized that the last one would only regenerate the XML file once (which could still be bad).  This one will hopefully regenerate it until it gets a good one.  I've also added logrotate setting to manage the log file and fixed a bug in the log file generation that made the starting time and ending times report as the same.  This version should have 0ubuntu5 in the version number

---

### Post by slick666 on 2009-01-28
Ok, guys I'm almost there. I got the XML generated, got it installed but all Movies seem to last only about 8 to 10 seconds. I don't have a cmd line capture yet. But there are a whole lot of

Cannot sync MAD frame.

Any ideas?

---

### Post by iitywygms on 2009-01-28
Yeah!  Today it works again.
To fix remote problem.  Changed video player to internal.
To fix this error  "cp: cannot create regular file `/var/www/hulu.xml': Permission denied"
I edited hulu-maker-xml and changed 

this

#!/bin/bash

rm /tmp/hulu.xml
su mythtv -c "gethulu.pl /tmp/hulu.xml"
su mythtv -c "cp /tmp/hulu.xml /var/www/"

to this

#!/bin/bash

rm /tmp/hulu.xml
su kevin -c "gethulu.pl /tmp/hulu.xml"
su kevin -c "cp /tmp/hulu.xml /var/www/"

Now everything seems fine.  I had this working fine for one day then it did not work for one day until I changed the above.

Maybe this is not the best way but it works for me.
If someone has input as to why the old way did not work, maybe that would be helpful?

---

### Post by iitywygms on 2009-01-28
I just downloaded the new version of hulu-xml-maker.

I assume I need to switch mythtv with kevin again.  Doing this will not cause any problems will it??

---

### Post by tgm4883 on 2009-01-28
> **iitywygms said:**
> Yeah!  Today it works again.
To fix remote problem.  Changed video player to internal.
To fix this error  "cp: cannot create regular file `/var/www/hulu.xml': Permission denied"
I edited hulu-maker-xml and changed 

this

#!/bin/bash

rm /tmp/hulu.xml
su mythtv -c "gethulu.pl /tmp/hulu.xml"
su mythtv -c "cp /tmp/hulu.xml /var/www/"

to this

#!/bin/bash

rm /tmp/hulu.xml
su kevin -c "gethulu.pl /tmp/hulu.xml"
su kevin -c "cp /tmp/hulu.xml /var/www/"

Now everything seems fine.  I had this working fine for one day then it did not work for one day until I changed the above.

Maybe this is not the best way but it works for me.
If someone has input as to why the old way did not work, maybe that would be helpful?

Thats odd, are you sure you are in the mythtv group?

---

### Post by iitywygms on 2009-01-28
> **tgm4883 said:**
> Thats odd, are you sure you are in the mythtv group?

Yeah I am.
Something is strange with my setup.  I can't put my finger on it.
Examples.
Sometimes when I exit the frontend, I have lost my administrative rights.  I can't unlock users and groups for example.
I also noticed lately, after running hulu-xml-maker, my desktop start bar would change.  The normal pop-up menu would not be displayed.  Instead it is replaced with a generic xfe menu.  I have to log out then back in for it to reset.
I have no idea what is causing this or how to even troubleshoot it.  I would start a new thread if I knew what to ask?????????  It only happens when I am messing with stuff, like adding mythvodka, the rest of the time it seems normal.  I can update without issues.  Any suggestions on what to check? Or should this be asked in a new thread?

---

### Post by slick666 on 2009-01-28
ok guys, sorry to be a little behind you all.

Here is the output I'm getting when I have the video problem
> 
2009-01-28 22:23:13.958 Running Command: /usr/bin/playstream.sh /usr/bin/curl /usr/bin/mencoder [http://www.podtrac.com/pts/redirect.avi/bitcast-a.bitgravity.com/revision3/web/systm/0084/systm--0084--dvdripping--large.xvid.avi](http://www.podtrac.com/pts/redirect.avi/bitcast-a.bitgravity.com/revision3/web/systm/0084/systm--0084--dvdripping--large.xvid.avi)
2009-01-28 22:23:13.959 Buffer Required: 3000000
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 44, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Playing /var/tmp/stream.mpg.

MPEG-PS file format detected.
VIDEO:  MPEG2  640x360  (aspect 1)  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 640 x 360 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 32.0 kbit/2.27% (ratio: 4000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 360 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 640x360 => 640x360 Planar YV12  [fs] [zoom]
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame

GNOME screensaver enabled

Exiting... (End of file)
2009-01-28 22:23:49.066 Selection: File: [http://www.podtrac.com/pts/redirect.avi/bitcast-a.bitgravity.com/revision3/web/systm/0084/systm--0084--dvdripping--large.xvid.avi](http://www.podtrac.com/pts/redirect.avi/bitcast-a.bitgravity.com/revision3/web/systm/0084/systm--0084--dvdripping--large.xvid.avi)


I'm not sure how to start figuring this out. Everything SEEMS to be going fine then the stream simply closes. It does not cause the front end to crash though. I've been able to repeat this with almost every category (hulu, BBC, etc.) If someone could clue me into when could be failing it would be much appreciated.

---

### Post by iitywygms on 2009-01-28
> **slick666 said:**
> ok guys, sorry to be a little behind you all.

Here is the output I'm getting when I have the video problem


I'm not sure how to start figuring this out. Everything SEEMS to be going fine then the stream simply closes. It does not cause the front end to crash though. I've been able to repeat this with almost every category (hulu, BBC, etc.) If someone could clue me into when could be failing it would be much appreciated.

Just a guess but isnt a madd error a mplayer error?  Have you tried using the internal player instead?
Sorry I can't be more help.

---

### Post by iitywygms on 2009-01-29
mistake

---

### Post by nrune on 2009-01-29
Many thanks to all who wrote and helped get this plugin running! 
Big thanks to tgm4883 for all his work and making the deb. It does a great job at hulu and revision 3 content!  What a great community.

 Mike

---

### Post by slick666 on 2009-01-29
> Just a guess but isnt a madd error a mplayer error? Have you tried using the internal player instead?
Sorry I can't be more help. 

Your right. I only round this thread that seemed to talk about it. I will have to pull it apart some more in a few hrs when I get back from work.

[http://ubuntuforums.org/showthread.php?t=669014]("http://ubuntuforums.org/showthread.php?t=669014")

---

### Post by iitywygms on 2009-01-29
New error today.
/usr/bin/hulu-scan.py: /bin/cat: /tmp/hulu.xml: No such file or directory
Check MythVodka Settings.
This happened when I opened mythvodka and it scanned up to 40%
I saved the old hulu-xml-maker so I will use that until someone suggest a different fix.

---

### Post by august495 on 2009-01-29
Same here with recent hulu-xml-maker. My CL output looks this same as post 196.

---

### Post by iitywygms on 2009-01-30
Just another note

I completely purged everything and reinstalled.

This is the latest.

kevin@mythtv:~$ sudo  /etc/cron.daily/hulu-xml-maker
[sudo] password for kevin: 
tail: cannot open `hulu.xml' for reading: No such file or directory
***** Starting regeneration of XML file on 21:57 01/29/2009 *****

The above message appears after about an hour.

One other note.  This may keep running forever. I will remove it from my cron jobs until I can figure out what the bleep is wrong with my system.
I don't think it is mythvodka, I think it is my system.

Edit:
What is really strange is that the file is there??  And what is nogroup?

kevin@mythtv:/tmp$ ls -l hulu.xml 
-rw-r--r-- 1 mythtv nogroup 16384 2009-01-29 22:08 hulu.xml

---

### Post by tgm4883 on 2009-01-30
> **august495 said:**
> Same here with recent hulu-xml-maker. My CL output looks this same as post 196.

> **iitywygms said:**
> Just another note

I completely purged everything and reinstalled.

This is the latest.

kevin@mythtv:~$ sudo  /etc/cron.daily/hulu-xml-maker
[sudo] password for kevin: 
tail: cannot open `hulu.xml' for reading: No such file or directory
***** Starting regeneration of XML file on 21:57 01/29/2009 *****

The above message appears after about an hour.

One other note.  This may keep running forever. I will remove it from my cron jobs until I can figure out what the bleep is wrong with my system.
I don't think it is mythvodka, I think it is my system.

Edit:
What is really strange is that the file is there??  And what is nogroup?

kevin@mythtv:/tmp$ ls -l hulu.xml 
-rw-r--r-- 1 mythtv nogroup 16384 2009-01-29 22:08 hulu.xml

My bad.  I didn't have the full path on the error checking (was looking at hulu.xml not /tmp/hulu.xml).  I've just pushed a fix for that and also the regenerating loop will only run 3 times in a row now.  I've also changed copying the xml file to a move as root per an email I received about that.

Grab the latest from the PPA, the new version is 1-0ubuntu7 and should be built in a few minutes.

---

### Post by tgm4883 on 2009-01-30
Arg, I just realized that hulu-xml-generator contained an old version of the episode title patch, so shows that used the same episode titles as other shows had issues.  I've fixed this in 0ubuntu8

---

### Post by tgm4883 on 2009-01-30
> **tgm4883 said:**
> Arg, I just realized that hulu-xml-generator contained an old version of the episode title patch, so shows that used the same episode titles as other shows had issues.  I've fixed this in 0ubuntu8

Just a friendly warning.  I plan on changing the name of hulu-xml-generator to mythvodka-hulu-generator in the next few days.  My reason for this is so that the mythvodka package will build this package also and they will share the same code base (rather than me copying patches to two locations).  This will help prevent issues like the one I quoted from happening.  I'll mark the new one as replacing the old one, and have them conflict with one another so that A) you won't have both installed at the same time and B) you should get a warning when doing apt-get upgrade that it has been replaced by the new package.  It might just upgrade you to the new package, but i'm not real sure on that.

---

### Post by august495 on 2009-01-30
0ubuntu8 fixed my issues! Thanks tgm4883!

---

### Post by iitywygms on 2009-01-30
So who is the CREATOR of this fine package?  It takes a lot of effort and time to create something like this.  I would like to kick down some bones to the architect if possible.  Also, is there a place to offer suggested options?

---

### Post by tgm4883 on 2009-01-30
> **iitywygms said:**
> So who is the CREATOR of this fine package?  It takes a lot of effort and time to create something like this.  I would like to kick down some bones to the architect if possible.  Also, is there a place to offer suggested options?

At the moment, vv1gg1 is taking credit for the plugin (in [post 18]("http://ubuntuforums.org/showpost.php?p=6463177&postcount=18")

Have you tried 0ubuntu8 yet?  I'm curious to know if it fixed your issue.

---

### Post by vv1gg1 on 2009-01-31
heyas

project now has a googlecode page

[http://code.google.com/p/mythvodka/](http://code.google.com/p/mythvodka/)

if anyone wants to be a member and contribute let me know

---

### Post by slick666 on 2009-01-31
Yea google ;)

---

### Post by tgm4883 on 2009-01-31
I've now made the merge of hulu-xml-generator into mythvodka.  The way that I have it done I believe that it will automatically upgrade people to the new package name.  I'll test this and report back.

---

### Post by iitywygms on 2009-01-31
> **tgm4883 said:**
> At the moment, vv1gg1 is taking credit for the plugin (in [post 18]("http://ubuntuforums.org/showpost.php?p=6463177&postcount=18")

Have you tried 0ubuntu8 yet?  I'm curious to know if it fixed your issue.
 
Yes it seems to work great now.  Special thank to all who helped and especially tgm4883.

---

### Post by fuchur on 2009-01-31
First of all, thanks to all contribuing to that program - its probably the best mythtv plugin around, and thanks to this thread and the ppa i could install got it working at the 2nd try...

But here is my problem/suggestion:

I watched a movie on hulu today, and after 1 hour it suddenly exited. I suspect it is related to the problem described somewhere on page 14 or so - the buffer just runs out of material, and thus the player exits.

This was quite annoying, as a could not jump back I had to go to hulu.com and finish it there. 
So my question is whether there is any way to avoid that. Not knowing much about the interals, I think an easy solution is to add an option to allow the player just to pause if it is at the end of the file. if that is not possible, anything that does not exit the player would be fine as well. 
After the movie had in fact ended, I guess i would have to press some button than to return to myth, but that would be fine.


This would also help if I want to skip some parts of a program - currently I am not sure I far I can jump ahead without risking to exit accidentally.


Alternatively, the behaviour of the program itself could be changed to add the movies to mythvideo or to the myth-tv recordings database (although i guess thats more complicated), so they can be played from there at any time


Would be great if there was any solution to that problem

---

### Post by gbutters on 2009-01-31
> **tgm4883 said:**
> I've now made the merge of hulu-xml-generator into mythvodka.  The way that I have it done I believe that it will automatically upgrade people to the new package name.  I'll test this and report back.

E: /var/cache/apt/archives/mythvodka-hulu-generator_07-0ubuntu27~jaunty_i386.deb: trying to overwrite `/usr/bin/gethulu.pl', which is also in package hulu-xml-maker

Had to remove hulu-xml-maker to get it to install

---

### Post by modorf on 2009-02-01
Thomas,

I upgraded from mythvodka_07-ubuntu25~hardy_amd64 to mythvodka_07-0ubuntu28~hardy_amd64 and mythvodka disappeared from the media library menu.  

After looking through the deb package and and my /usr/lib/mythtv/plugins directory, it seems that the libmythvodka.so file is missing.

Can you please update the package with the plugin library file.

Thanks.

---

### Post by tgm4883 on 2009-02-02
> **modorf said:**
> Thomas,

I upgraded from mythvodka_07-ubuntu25~hardy_amd64 to mythvodka_07-0ubuntu28~hardy_amd64 and mythvodka disappeared from the media library menu.  

After looking through the deb package and and my /usr/lib/mythtv/plugins directory, it seems that the libmythvodka.so file is missing.

Can you please update the package with the plugin library file.

Thanks.

Whoops, side effect of building multiple binaries that I didn't know about.  Fixed in 0ubuntu29

---

### Post by modorf on 2009-02-02
thanks for the rebuild the lib is working.
I found a new set of missing files with build 29.
There is no streams-ui.xml files.
The two files shoul be: 
/usr/share/mythtv/themes/default/streams-ui.xml
/usr/share/mythtv/themes/default-wide/streams-ui.xml

I was able to grab them from the source tar file.
After copying them in, Mythvodka seems to be working.  I just tested with Revision3 and Hulu.

Any idea as to what is needed to be configured to get NZB working?


Thanks.

---

### Post by tgm4883 on 2009-02-02
> **modorf said:**
> thanks for the rebuild the lib is working.
I found a new set of missing files with build 29.
There is no streams-ui.xml files.
The two files shoul be: 
/usr/share/mythtv/themes/default/streams-ui.xml
/usr/share/mythtv/themes/default-wide/streams-ui.xml

I was able to grab them from the source tar file.
After copying them in, Mythvodka seems to be working.  I just tested with Revision3 and Hulu.

Any idea as to what is needed to be configured to get NZB working?


Thanks.

Yea I just saw that.  I'm pushing an update (0ubuntu30) that I believe will fix all the missing files.

On one of these pages in this thread there was info on how to get the NZB working, but I didn't incorporate it as it has no interest to me.

---

### Post by iitywygms on 2009-02-02
Other than new packaging, is there a reason to upgrade to latest package?

---

### Post by tgm4883 on 2009-02-02
> **iitywygms said:**
> Other than new packaging, is there a reason to upgrade to latest package?

no

---

### Post by lerrup on 2009-02-02
I'd really like to get this to work, but have had some reasonably crucial problems.

I've tried to use the ppa, but the .deb's not showing:  I think there's been a problem with the build-is that right.

Secondly, I tried the instructions on the mythtv wiki, but it keeps chucking up errors when I tried to gzip the file.

Any ideas?

Or is there an easier way to do this?

---

### Post by tgm4883 on 2009-02-02
> **lerrup said:**
> I'd really like to get this to work, but have had some reasonably crucial problems.

I've tried to use the ppa, but the .deb's not showing:  I think there's been a problem with the build-is that right.

Secondly, I tried the instructions on the mythtv wiki, but it keeps chucking up errors when I tried to gzip the file.

Any ideas?

Or is there an easier way to do this?

PPA should be fine, what Ubuntu Release are you using?

---

### Post by fuchur on 2009-02-03
i just update to the most current version, and now is get

"cannot locate "streamsui" in theme "stream-"" and mythvodka quits the mythfrorntend. I did not make any change besides upgrading mythvodka.

---

### Post by tgm4883 on 2009-02-03
> **fuchur said:**
> i just update to the most current version, and now is get

"cannot locate "streamsui" in theme "stream-"" and mythvodka quits the mythfrorntend. I did not make any change besides upgrading mythvodka.

Are you running the 0ubuntu30 version?  That sounds like the bug from 0ubuntu29.  Which ubuntu release are you on?

---

### Post by fuchur on 2009-02-03
sory, appearently forgot to refresh database before updating. Newest version fixes that. Thank you

Still, I would be interested to know if there is a way to prevent mythvodka from exiting if it runs out of buffer.

---

### Post by marc.aronson on 2009-02-03
> **fuchur said:**
> Still, I would be interested to know if there is a way to prevent mythvodka from exiting if it runs out of buffer.

I've had that problem when I use the internal player. I switched to mplayer and I don't have that problem anymore -- mplayer simply pauses when it hits the end of the buffer. I did have to write a small wrapper around mplayer to work around the problem where the player would sometimes exit before playback began. You can extract a copy of it from the tar file that is attached to the knoppmyth wiki page at [http://www.knoppmythwiki.org/index.php?page=MythVodkaHowTo#InstallPrebuilt](http://www.knoppmythwiki.org/index.php?page=MythVodkaHowTo#InstallPrebuilt) -- the file you are looking for is in ./usr/local/bin/ and is called something like "mythvodka_player.sh".

There are also some fixes in ./usr/local/bin/hulu to fix a problem that results in some shows not playing.

---

### Post by fuchur on 2009-02-03
Thanks, I will look into that later, but it seems it should solve my problem.

---

### Post by scary_jeff on 2009-02-03
Hmm, I still can't get past my 'only plays the first 50 odd seconds' issue with iPlayer. Should I be running from the latest MythTV source for this to work properly? I'm running normal 0.21.

---

### Post by vv1gg1 on 2009-02-03
Anyone who has video play and then stop, your net connection isnt fast enough. If it can play even a second of video everything is in place, the only problem is it cant download fast enough, it plays to the end before it gets more data.

Only real solution is to increase timeouts, which I probably buried in the code... you might be able to add a "sleep 30" into the script that takes the flv and makes it into an MPEG2 so it buffers more before mythtv starts to play

---

### Post by modorf on 2009-02-04
> **tgm4883 said:**
> It use to grab it from [http://www.bewhere.co.uk/streams.xml](http://www.bewhere.co.uk/streams.xml) but if you go to that link, you will see nothing.  Probably why it has disappeared.

Anyone know who the maintainer of the streams.xml list is.
I am hoping to contact them to ask about updating the list of Revision3 shows.  There are two shows which are missing that I'm interested in: Hak5 and Scam School.

Thank you.

---

### Post by scary_jeff on 2009-02-04
> **vv1gg1 said:**
> Anyone who has video play and then stop, your net connection isnt fast enough. If it can play even a second of video everything is in place, the only problem is it cant download fast enough, it plays to the end before it gets more data.

Only real solution is to increase timeouts, which I probably buried in the code... you might be able to add a "sleep 30" into the script that takes the flv and makes it into an MPEG2 so it buffers more before mythtv starts to play

Thanks for the response.

I can watch high quality streams through iPlayer using the BBC website, with only a couple of seconds prebuffering time. Could my problem still be caused by connection speed? Perhaps BBC doesn't let you download as fast when not using their player?

---

### Post by lerrup on 2009-02-04
thanks for the help; the ppa seems to want to play and I've got it installed.

My next problem is that it crashes the frontend when loading at 40%.  The log reads: 
....................................................................................
2009-02-04 19:21:55.394 Inserting prog: Words and Pictures: Fun with Phonics
2009-02-04 19:21:55.403 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-02-04 19:21:55.414 Server returned an error status code 0 for url: 
2009-02-04 19:21:55.426 Inserting prog: Yoko! Jakamoko! Toto!
2009-02-04 19:21:55.439 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-02-04 19:21:55.449 Server returned an error status code 0 for url: 
2009-02-04 19:21:55.455 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-02-04 19:21:55.465 Server returned an error status code 0 for url: 
2009-02-04 19:21:55.482 Inserting prog: Animal Park: Series 9
2009-02-04 19:21:55.493 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-02-04 19:21:55.504 Server returned an error status code 0 for url: 
2009-02-04 19:21:55.583 Inserting prog: Nicholas Crane's Britannia: The Great Elizabethan Journey
2009-02-04 19:21:55.593 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-02-04 19:21:55.604 Server returned an error status code 0 for url: 
2009-02-04 19:21:55.638 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-02-04 19:21:55.648 Server returned an error status code 0 for url: 
2009-02-04 19:21:55.682 MythVodka Hulu Grabber: Executing '/usr/bin/hulu-scan.py'
2009-02-04 19:21:55.742 Grabber Finished. Processing Data.
2009-02-04 19:21:55.743 Error parsing data from grabber: Error: unexpected end of file Location Line: 1 Column 1


Any ideas?

---

### Post by iitywygms on 2009-02-04
You have the same error I did.
see post #157

---

### Post by bcg30506 on 2009-02-04
I've finally gotten this working for hulu and must say it is awesome.  Nice job!  I do have one issue though which I've not found an answer for here, and that is some shows do not play.  Most have so I know my setup must be good or at least very close.  One in particular is WKRP in Cincinnati "Turkeys Away" episode.  I immediately get an error saying this file cannot be streamed.  However, it plays fine in Firefox using the Flash plugin at the hulu.com site.

I ran the hulu script manually from the terminal to see what is happening using this command:

./hulu http://www.hulu.com/watch/322 /var/tmp/TurkeysAway.mov

and got this output:

http://releasegeo.hulu.com/content.select?pid=js_q_bh1pcyV6j0mv2mkkG7CvtD9-S6P&mbr=true&format=smil
stream url
rtmpdump --rtmp rtmp://cp47346.edgefcs.net:1935/ondemand?_fcs_vhost=cp47346.edgefcs.net\&auth=daEbFbVcyb8d8aocfdebwcWbpblchb2a8ch-bjIGum-4q-XoMDvDn1Axq\&aifp=sll02152008\&slist=hulufms3/47311/4/40/H264_1Mbps_TranscodeBacklog_10101__sAokzmRjs0SGYseQ+I34fw.flv --swfUrl http://www.hulu.com/player.swf?_r=828081233782027924 --pageUrl http://www.hulu.com/watch/322 --app ondemand?_fcs_vhost=cp47346.edgefcs.net -o /var/tmp/TurkeysAway.mov --tcUrl rtmp://cp47346.edgefcs.net:1935/ondemand?_fcs_vhost=cp47346.edgefcs.net\&auth=daEbFbVcyb8d8aocfdebwcWbpblchb2a8ch-bjIGum-4q-XoMDvDn1Axq\&aifp=sll02152008\&slist=hulufms3/47311/4/40/H264_1Mbps_TranscodeBacklog_10101__sAokzmRjs0SGYseQ+I34fw.flv\;.international=false
RTMP Dumper v1.3
(c) 2009 Andrej Stepanchuk, license: GPL

DEBUG: Setting buffer time to: 36000000ms
Connecting to rtmp://cp47346.edgefcs.net:1935/ondemand?_fcs_vhost=cp47346.edgefcs.net&auth=daEbFbVcyb8d8aocfdebwcWbpblchb2a8ch-bjIGum-4q-XoMDvDn1Axq&aifp=sll02152008&slist=hulufms3/47311/4/40/H264_1Mbps_TranscodeBacklog_10101__sAokzmRjs0SGYseQ+I34fw.flv ...
DEBUG: Hostname: cp47346.edgefcs.net
DEBUG: Port: 1935
DEBUG: connected, hand shake:
DEBUG: handshaked
Connected...

Starting download at 0.000 KB
DEBUG: GetNextMediaPacket, received: server BW
DEBUG: GetNextMediaPacket, received: client BW
DEBUG: server sent ping. type: 0
DEBUG: GetNextMediaPacket, received: invoke
DEBUG: Property: <Name:                  no-name., STRING:      _result>
DEBUG: Property: <Name:                  no-name., NUMBER:      1.00>
DEBUG: Property: <Name:                  no-name., OBJECT>
DEBUG: Property: <Name:                    fmsVer, STRING:      FMS/3,0,2,222>
DEBUG: Property: <Name:              capabilities, NUMBER:      31.00>
DEBUG: Property: <Name:                  no-name., OBJECT>
DEBUG: Property: <Name:                     level, STRING:      status>
DEBUG: Property: <Name:                      code, STRING:      NetConnection.Connect.Success>
DEBUG: Property: <Name:               description, STRING:      Connection succeeded.>
DEBUG: Property: <Name:            objectEncoding, NUMBER:      0.00>
DEBUG: HandleInvoke, server invoking <_result>
DEBUG: HandleInvoke, received result for method call <connect>
DEBUG: sending ping. type: 0x0003
DEBUG: GetNextMediaPacket, received: invoke
DEBUG: Property: <Name:                  no-name., STRING:      onBWDone>
DEBUG: Property: <Name:                  no-name., NUMBER:      0.00>
DEBUG: HandleInvoke, server invoking <onBWDone>
DEBUG: GetNextMediaPacket, received: invoke
DEBUG: Property: <Name:                  no-name., STRING:      _result>
DEBUG: Property: <Name:                  no-name., NUMBER:      2.00>
DEBUG: Property: NULL
DEBUG: Property: <Name:                  no-name., NUMBER:      1.00>
DEBUG: HandleInvoke, server invoking <_result>
DEBUG: HandleInvoke, received result for method call <createStream>
DEBUG: Sending play: hulufms3/47311/4/40/H264_1Mbps_TranscodeBacklog_10101__sAokzmRjs0SGYseQ+I34fw.flv
DEBUG: sending ping. type: 0x0003
DEBUG: server sent ping. type: 0
DEBUG: GetNextMediaPacket, received: invoke
DEBUG: Property: <Name:                  no-name., STRING:      onStatus>
DEBUG: Property: <Name:                  no-name., NUMBER:      0.00>
DEBUG: Property: NULL
DEBUG: Property: <Name:                  no-name., OBJECT>
DEBUG: Property: <Name:                     level, STRING:      error>
DEBUG: Property: <Name:                      code, STRING:      NetStream.Play.StreamNotFound>
DEBUG: Property: <Name:               description, STRING:      Failed to play hulufms3/47311/4/40/H264_1Mbps_TranscodeBacklog_10101__sAokzmRjs0SGYseQ+I34fw.flv; stream not found.>
DEBUG: Property: <Name:                   details, STRING:      hulufms3/47311/4/40/H264_1Mbps_TranscodeBacklog_10101__sAokzmRjs0SGYseQ+I34fw.flv>
DEBUG: Property: <Name:                  clientid, STRING:      a30YgH47>
DEBUG: HandleInvoke, server invoking <onStatus>
DEBUG: HandleInvoke, onStatus: NetStream.Play.StreamNotFound
DEBUG: GetNextMediaPacket, received: invoke
DEBUG: Property: <Name:                  no-name., STRING:      onStatus>
DEBUG: Property: <Name:                  no-name., NUMBER:      0.00>
DEBUG: Property: NULL
DEBUG: Property: <Name:                  no-name., OBJECT>
DEBUG: Property: <Name:                     level, STRING:      status>
DEBUG: Property: <Name:                      code, STRING:      NetStream.Play.Stop>
DEBUG: Property: <Name:               description, STRING:      Stopped playing hulufms3/47311/4/40/H264_1Mbps_TranscodeBacklog_10101__sAokzmRjs0SGYseQ+I34fw.flv.>
DEBUG: Property: <Name:                   details, STRING:      hulufms3/47311/4/40/H264_1Mbps_TranscodeBacklog_10101__sAokzmRjs0SGYseQ+I34fw.flv>
DEBUG: Property: <Name:                  clientid, STRING:      a30YgH47>
DEBUG: Property: <Name:                    reason, STRING:      >
DEBUG: HandleInvoke, server invoking <onStatus>
DEBUG: HandleInvoke, onStatus: NetStream.Play.Stop
Closing connection... done!

---

### Post by Boppy3125 on 2009-02-04
I have a master backend/frontend running MythBuntu 8.4.1 with just the regular updates pushed by Ubuntu.  I also have a Frontend only 8.10 MythBuntu in another room, if that matters.

So I am curious, can I install this on one box without causing problems on the other?  In other words, does it change anything in the database that would require me to install on both, or immeadiately invalidate the idea of future upgrades?  Not a problem just wanting to understand what I am getting into.  

Also, just to review, my easiest option to install is to just use [https://edge.launchpad.net/~tgm4883/+archive/ppa](https://edge.launchpad.net/~tgm4883/+archive/ppa) and what, install the MythVodka package?  (Obviously I am new to this PPA thing, I am reading up on it now.)  I would guess prerequisite would be a working flash system.  So if I can play hulu videos now in FireFox and my MythBuntu is working from the 8.10 install level, Am I ready to start?  am I missing anything?

---

### Post by Boppy3125 on 2009-02-04
> **lerrup said:**
> thanks for the help; the ppa seems to want to play and I've got it installed.

My next problem is that it crashes the frontend when loading at 40%.  The log reads: 
....................................................................................
2009-02-04 19:21:55.394 Inserting prog: Words and Pictures: Fun with Phonics
2009-02-04 19:21:55.403 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-02-04 19:21:55.414 Server returned an error status code 0 for url: 
2009-02-04 19:21:55.426 Inserting prog: Yoko! Jakamoko! Toto!
2009-02-04 19:21:55.439 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-02-04 19:21:55.449 Server returned an error status code 0 for url: 
2009-02-04 19:21:55.455 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-02-04 19:21:55.465 Server returned an error status code 0 for url: 
2009-02-04 19:21:55.482 Inserting prog: Animal Park: Series 9
2009-02-04 19:21:55.493 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-02-04 19:21:55.504 Server returned an error status code 0 for url: 
2009-02-04 19:21:55.583 Inserting prog: Nicholas Crane's Britannia: The Great Elizabethan Journey
2009-02-04 19:21:55.593 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-02-04 19:21:55.604 Server returned an error status code 0 for url: 
2009-02-04 19:21:55.638 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-02-04 19:21:55.648 Server returned an error status code 0 for url: 
2009-02-04 19:21:55.682 MythVodka Hulu Grabber: Executing '/usr/bin/hulu-scan.py'
2009-02-04 19:21:55.742 Grabber Finished. Processing Data.
2009-02-04 19:21:55.743 Error parsing data from grabber: Error: unexpected end of file Location Line: 1 Column 1


Any ideas?


I also used the PPA, left everything defaults, verified the paths to things in the settings page and then after 30 sec to a minute, frontend crashed with the same log info.

--
I think I found it in post #157, but slightly revised with the updates.
sudo /etc/cron.daily/mythvodka-hulu-generator
Now just waiting for the command to complete.

---

### Post by bcg30506 on 2009-02-05
> **bcg30506 said:**
> I've finally gotten this working for hulu and must say it is awesome.  Nice job!  I do have one issue though which I've not found an answer for here, and that is some shows do not play.  Most have so I know my setup must be good or at least very close.  One in particular is WKRP in Cincinnati "Turkeys Away" episode.  I immediately get an error saying this file cannot be streamed.  However, it plays fine in Firefox using the Flash plugin at the hulu.com site.

I ran the hulu script manually from the terminal to see what is happening using this command:

./hulu [http://www.hulu.com/watch/322](http://www.hulu.com/watch/322) /var/tmp/TurkeysAway.mov

and got this output:

[http://releasegeo.hulu.com/content.select?pid=js_q_bh1pcyV6j0mv2mkkG7CvtD9-S6P&mbr=true&format=smil](http://releasegeo.hulu.com/content.select?pid=js_q_bh1pcyV6j0mv2mkkG7CvtD9-S6P&mbr=true&format=smil)
stream url
rtmpdump --rtmp rtmp://cp47346.edgefcs.net:1935/ondemand?_fcs_vhost=cp47346.edgefcs.net\&auth=daEbFbVcyb8d8aocfdebwcWbpblchb2a8ch-bjIGum-4q-XoMDvDn1Axq\&aifp=sll02152008\&slist=hulufms3/47311/4/40/H264_1Mbps_TranscodeBacklog_10101__sAokzmRjs0SGYseQ+I34fw.flv --swfUrl [http://www.hulu.com/player.swf?_r=828081233782027924](http://www.hulu.com/player.swf?_r=828081233782027924) --pageUrl [http://www.hulu.com/watch/322](http://www.hulu.com/watch/322) --app ondemand?_fcs_vhost=cp47346.edgefcs.net -o /var/tmp/TurkeysAway.mov --tcUrl rtmp://cp47346.edgefcs.net:1935/ondemand?_fcs_vhost=cp47346.edgefcs.net\&auth=daEbFbVcyb8d8aocfdebwcWbpblchb2a8ch-bjIGum-4q-XoMDvDn1Axq\&aifp=sll02152008\&slist=hulufms3/47311/4/40/H264_1Mbps_TranscodeBacklog_10101__sAokzmRjs0SGYseQ+I34fw.flv\;.international=false
RTMP Dumper v1.3
(c) 2009 Andrej Stepanchuk, license: GPL

DEBUG: Setting buffer time to: 36000000ms
Connecting to rtmp://cp47346.edgefcs.net:1935/ondemand?_fcs_vhost=cp47346.edgefcs.net&auth=daEbFbVcyb8d8aocfdebwcWbpblchb2a8ch-bjIGum-4q-XoMDvDn1Axq&aifp=sll02152008&slist=hulufms3/47311/4/40/H264_1Mbps_TranscodeBacklog_10101__sAokzmRjs0SGYseQ+I34fw.flv ...
DEBUG: Hostname: cp47346.edgefcs.net
DEBUG: Port: 1935
DEBUG: connected, hand shake:
DEBUG: handshaked
Connected...

Starting download at 0.000 KB
DEBUG: GetNextMediaPacket, received: server BW
DEBUG: GetNextMediaPacket, received: client BW
DEBUG: server sent ping. type: 0
DEBUG: GetNextMediaPacket, received: invoke
DEBUG: Property: <Name:                  no-name., STRING:      _result>
DEBUG: Property: <Name:                  no-name., NUMBER:      1.00>
DEBUG: Property: <Name:                  no-name., OBJECT>
DEBUG: Property: <Name:                    fmsVer, STRING:      FMS/3,0,2,222>
DEBUG: Property: <Name:              capabilities, NUMBER:      31.00>
DEBUG: Property: <Name:                  no-name., OBJECT>
DEBUG: Property: <Name:                     level, STRING:      status>
DEBUG: Property: <Name:                      code, STRING:      NetConnection.Connect.Success>
DEBUG: Property: <Name:               description, STRING:      Connection succeeded.>
DEBUG: Property: <Name:            objectEncoding, NUMBER:      0.00>
DEBUG: HandleInvoke, server invoking <_result>
DEBUG: HandleInvoke, received result for method call <connect>
DEBUG: sending ping. type: 0x0003
DEBUG: GetNextMediaPacket, received: invoke
DEBUG: Property: <Name:                  no-name., STRING:      onBWDone>
DEBUG: Property: <Name:                  no-name., NUMBER:      0.00>
DEBUG: HandleInvoke, server invoking <onBWDone>
DEBUG: GetNextMediaPacket, received: invoke
DEBUG: Property: <Name:                  no-name., STRING:      _result>
DEBUG: Property: <Name:                  no-name., NUMBER:      2.00>
DEBUG: Property: NULL
DEBUG: Property: <Name:                  no-name., NUMBER:      1.00>
DEBUG: HandleInvoke, server invoking <_result>
DEBUG: HandleInvoke, received result for method call <createStream>
DEBUG: Sending play: hulufms3/47311/4/40/H264_1Mbps_TranscodeBacklog_10101__sAokzmRjs0SGYseQ+I34fw.flv
DEBUG: sending ping. type: 0x0003
DEBUG: server sent ping. type: 0
DEBUG: GetNextMediaPacket, received: invoke
DEBUG: Property: <Name:                  no-name., STRING:      onStatus>
DEBUG: Property: <Name:                  no-name., NUMBER:      0.00>
DEBUG: Property: NULL
DEBUG: Property: <Name:                  no-name., OBJECT>
DEBUG: Property: <Name:                     level, STRING:      error>
DEBUG: Property: <Name:                      code, STRING:      NetStream.Play.StreamNotFound>
DEBUG: Property: <Name:               description, STRING:      Failed to play hulufms3/47311/4/40/H264_1Mbps_TranscodeBacklog_10101__sAokzmRjs0SGYseQ+I34fw.flv; stream not found.>
DEBUG: Property: <Name:                   details, STRING:      hulufms3/47311/4/40/H264_1Mbps_TranscodeBacklog_10101__sAokzmRjs0SGYseQ+I34fw.flv>
DEBUG: Property: <Name:                  clientid, STRING:      a30YgH47>
DEBUG: HandleInvoke, server invoking <onStatus>
DEBUG: HandleInvoke, onStatus: NetStream.Play.StreamNotFound
DEBUG: GetNextMediaPacket, received: invoke
DEBUG: Property: <Name:                  no-name., STRING:      onStatus>
DEBUG: Property: <Name:                  no-name., NUMBER:      0.00>
DEBUG: Property: NULL
DEBUG: Property: <Name:                  no-name., OBJECT>
DEBUG: Property: <Name:                     level, STRING:      status>
DEBUG: Property: <Name:                      code, STRING:      NetStream.Play.Stop>
DEBUG: Property: <Name:               description, STRING:      Stopped playing hulufms3/47311/4/40/H264_1Mbps_TranscodeBacklog_10101__sAokzmRjs0SGYseQ+I34fw.flv.>
DEBUG: Property: <Name:                   details, STRING:      hulufms3/47311/4/40/H264_1Mbps_TranscodeBacklog_10101__sAokzmRjs0SGYseQ+I34fw.flv>
DEBUG: Property: <Name:                  clientid, STRING:      a30YgH47>
DEBUG: Property: <Name:                    reason, STRING:      >
DEBUG: HandleInvoke, server invoking <onStatus>
DEBUG: HandleInvoke, onStatus: NetStream.Play.Stop
Closing connection... done!

I found a thread on a forum for another piece of software similar to mythvodka but for Windows that had this same issue.  According to them, it is an authentication issue.  Evidently some shows on hulu require RTMPE encryption and rtmpdump doesn't handle it while the flash player browser plugin does?  Does this mean mythvodka's lifespan is short in the U.S. due to media industry wanted to protect everything?  Is hulu on borrowed time as well?  Any workarounds for this?

---

### Post by iitywygms on 2009-02-05
I have a situation like the one posted above.  I went to watch 24 and when I pressed play, nothing happened.  No error messages or anything.  So I try something different, Babylon 5.  This worked without issue.  So some programs work and some don't.
Is this a mythvodka issue or Hulu???

---

### Post by marc.aronson on 2009-02-06
> **iitywygms said:**
> I have a situation like the one posted above.  I went to watch 24 and when I pressed play, nothing happened.  No error messages or anything.  So I try something different, Babylon 5.  This worked without issue.  So some programs work and some don't.
Is this a mythvodka issue or Hulu???

The problem is in the script "/usr/local/bin/hulu". I explained how to fit it in this post: [http://ubuntuforums.org/showpost.php?p=6669397&postcount=220](http://ubuntuforums.org/showpost.php?p=6669397&postcount=220)

---

### Post by iitywygms on 2009-02-06
> **marc.aronson said:**
> The problem is in the script "/usr/local/bin/hulu". I explained how to fit it in this post: [http://ubuntuforums.org/showpost.php?p=6669397&postcount=220](http://ubuntuforums.org/showpost.php?p=6669397&postcount=220)

I don't think that is the same problem.  I am not experiencing any crashes or errors.  It's just that when I try to play certain streams, nothing happens.

---

### Post by marc.aronson on 2009-02-06
> **iitywygms said:**
> I don't think that is the same problem.  I am not experiencing any crashes or errors.  It's just that when I try to play certain streams, nothing happens.

Please see the second paragraph: 
[INDENT][I]There are also some fixes in ./usr/local/bin/hulu to fix a problem that results in some shows not playing.
[/I][/INDENT]
Not an issue of crashes or errors. It fixes a problem where certain shows will not play. I have attached a tar file ("hulu.gz") to this post with the single file "hulu" in it -- md5sum is d9fef0caa552624c2eb6c233d2e17746. To install:

[LIST=1]
[*]cd /tmp; tar -xzf hulu.gz
[*]mv /usr/local/bin/hulu  /usr/local/bin/hulu.save
[*]cp hulu /usr/local/bin/hulu; chmod a+x /usr/local/bin/hulu
[*]mkdir /var/log/mythtv
[*]chmod a+rwx /var/log/mythtv
[/LIST]

---

### Post by bcg30506 on 2009-02-06
> **marc.aronson said:**
> Please see the second paragraph: 
[INDENT][I]There are also some fixes in ./usr/local/bin/hulu to fix a problem that results in some shows not playing.
[/I][/INDENT]
Not an issue of crashes or errors. It fixes a problem where certain shows will not play. I have attached a tar file ("hulu.gz") to this post with the single file "hulu" in it -- md5sum is d9fef0caa552624c2eb6c233d2e17746. To install:

[LIST=1]
[*]cd /tmp; tar -xzf hulu.gz
[*]mv /usr/local/bin/hulu  /usr/local/bin/hulu.save
[*]cp hulu /usr/local/bin/hulu; chmod a+x /usr/local/bin/hulu
[*]mkdir /var/log/mythtv
[*]chmod a+rw /var/log/mythtv
[/LIST]

A few things:

1. I was already using the player script and that did solve my end of buffer errors.
2. The script contained in the gz file has binary junk at the start and end which I had to clean up in vi before trying.
3. The new hulu script did not solve the problem I have trying to play WKRP in Cincinnati.  I can play the shows fine in Firefox using the Flash plugin.  It appears rtmpdump is erroring out with a message about needing RTMPE or RTMPTE -maybe some type of encryption on some videos?

---

### Post by tgm4883 on 2009-02-06
> **bcg30506 said:**
> A few things:

1. I was already using the player script and that did solve my end of buffer errors.
2. The script contained in the gz file has binary junk at the start and end which I had to clean up in vi before trying.
3. The new hulu script did not solve the problem I have trying to play WKRP in Cincinnati.  I can play the shows fine in Firefox using the Flash plugin.  It appears rtmpdump is erroring out with a message about needing RTMPE or RTMPTE -maybe some type of encryption on some videos?

I haven't tested the script he posted, but I don't see any junk in the beginning or end.  Did you gunzip the file before looking in it?

---

### Post by marc.aronson on 2009-02-06
1. Per instruction in post, please use tar to process the file. It is a gzip'ed tarfile. I forgot that "gz" is for zipped files, not gziped tar files.

2. If you are able to play back at least 1 frame of the show, then these changes won't solve any subsequent problems you may encounter. This change fixes one problem: There are some files where playback never successfully starts.

---

### Post by bcg30506 on 2009-02-06
> **marc.aronson said:**
> 1. Per instruction in post, please use tar to process the file. It is a gzip'ed tarfile. I forgot that "gz" is for zipped files, not gziped tar files.

2. If you are able to play back at least 1 frame of the show, then these changes won't solve any subsequent problems you may encounter. This change fixes one problem: There are some files where playback never successfully starts.

I gunzipped, did not use tar xzf.  I can try that and see if it works then.  I have the 2nd problem you mention, playback never starts for some shows.  I get the window saying "Oh No!" after a few seconds of it trying to buffer the video.

---

### Post by bcg30506 on 2009-02-06
Saved it as a tar.gz file and used tar xzf on it to get the script.  It was identical to what I had fixed in vi and I get the same results trying to play WKRP.

---

### Post by scary_jeff on 2009-02-06
> **scary_jeff said:**
> Thanks for the response.

I can watch high quality streams through iPlayer using the BBC website, with only a couple of seconds prebuffering time. Could my problem still be caused by connection speed? Perhaps BBC doesn't let you download as fast when not using their player?

Just been having another go at getting this working. I refreshed /var/tmp while trying to watch a stream:
During the initial buffering, iplayerdump.partial.mov steadily increases in size. When the buffering finishes, stream.mpg is created, and rapidly reaches a size of 10 megs or so. The mov file carries on getting bigger. If I pause the playback, the partial file will carry on getting bigger and bigger, but even after leaving it for 5 minutes (by which time the partial file is over 50 megabytes), the stream.mpg never changes size, and I can't watch past the first 30 seconds or so having unpaused. It just doesn't seem to be doing anything with the data that it downloads after the initial buffering stage.
Is stream.mpg even the file I'm watching?

---

### Post by iitywygms on 2009-02-06
I made no changes and now everything is working good.  Hmm, I think I will  shut up now and be satisfied.  This app is great even if it has small bugs.:popcorn:

---

### Post by lerrup on 2009-02-07
Thanks so far,  I might be getting somewhere, not sure where...

I've installed mythvodka-hulu-generator and when I run the cron job, I get the following errors:

blurb@box:~$ sudo /etc/cron.daily/mythvodka-hulu-generator

rm: cannot remove `/tmp/hulu.xml': No such file or directory
sh: cannot create /var/log/mythtv/mythvodka-hulu-generator.log: Permission denied
sh: cannot create /var/log/mythtv/mythvodka-hulu-generator.log: Permission denied
sh: cannot create /var/log/mythtv/mythvodka-hulu-generator.log: Permission denied
sh: cannot create /var/log/mythtv/mythvodka-hulu-generator.log: Permission denied
tail: cannot open `/tmp/hulu.xml' for reading: No such file or directory
sh: cannot create /var/log/mythtv/mythvodka-hulu-generator.log: Permission denied
sh: cannot create /var/log/mythtv/mythvodka-hulu-generator.log: Permission denied
sh: cannot create /var/log/mythtv/mythvodka-hulu-generator.log: Permission denied
sh: cannot create /var/log/mythtv/mythvodka-hulu-generator.log: Permission denied
sh: cannot create /var/log/mythtv/mythvodka-hulu-generator.log: Permission denied
sh: cannot create /var/log/mythtv/mythvodka-hulu-generator.log: Permission denied
sh: cannot create /var/log/mythtv/mythvodka-hulu-generator.log: Permission denied
sh: cannot create /var/log/mythtv/mythvodka-hulu-generator.log: Permission denied
sh: cannot create /var/log/mythtv/mythvodka-hulu-generator.log: Permission denied
************************************* >> /var/log/mythtv/mythvodka-hulu-generator.log
***** ERROR: XML File is broken ***** >> /var/log/mythtv/mythvodka-hulu-generator.log
************************************* >> /var/log/mythtv/mythvodka-hulu-generator.log


So I waited for it to do itself and so now get the following in /var/log/mythtv/mythvodka-hulu-generator.log:

rm: cannot remove `/tmp/hulu.xml': No such file or directory
rm: cannot remove `/tmp/hulu.xml': No such file or directory
rm: cannot remove `/tmp/hulu.xml': No such file or directory
rm: cannot remove `/tmp/hulu.xml': No such file or directory
rm: cannot remove `/tmp/hulu.xml': No such file or directory
rm: cannot remove `/tmp/hulu.xml': No such file or directory

The frontend log exits with:

....2009-02-06 23:25:20.927 MythVodka Data Grabber: Executing '/usr/local/bin/get_iplayer -q --mythtv - --xml-channels'
2009-02-06 23:25:27.242 Grabber Finished. Processing Data.
2009-02-06 23:25:27.244 Error parsing data from grabber: Error: letter is expected Location Line: 273 Column 15

Any ideas?

*some time later*

a few moments reflection led me to the thought that what was needed was the log file permissions to be changed.  I have now changed this to user mythtv and the cron job seems to be running okay....

*some time later again*

it still crashes out,  the error I get is:

009-02-07 18:41:29.015 HttpComms::done() - NetworkOperation Error on Finish: No server set to connect to (1): url: 'file:/'
2009-02-07 18:41:29.025 Server returned an error status code 0 for url: 
2009-02-07 18:41:29.031 MythVodka Data Grabber: Executing '/usr/local/bin/get_iplayer -q --mythtv - --xml-channels'
2009-02-07 18:41:30.427 Grabber Finished. Processing Data.
2009-02-07 18:41:30.429 Error parsing data from grabber: Error: letter is expected Location Line: 277 Column 15

Also, if I get this working, where's the BBC data?  I'm in the UK and it doesn't seem to be anywhere.:confused:

---

### Post by Fmstrat on 2009-02-12
I'm having a compilation problem.  I'm running an SVN release from a while ago of 0.21, so I'm not sure that installing a mythlib-dev package is even possible for me.

After compiling mythplugins sucessfully, then copying the mythvodka folder in, I get this on make:

cd mythvodka && make -f Makefile
make[1]: Entering directory `/opt/Software/mythtv_svn/mythplugins/mythvodka/mythvodka'
g++ -c -pipe -march=k8 -pthread -I/usr/include/kde/artsc -I/usr/include/glib-2.0 -I/usr/lib64/glib-2.0/include -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -Wno-non-virtual-dtor -D__STDC_CONSTANT_MACROS -Wall -W -fomit-frame-pointer -O3 -fomit-frame-pointer -D_REENTRANT -DPIC -fPIC  -D_GNU_SOURCE -DPREFIX=\"/usr/local\" -DMMX -D_FILE_OFFSET_BITS=64 -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_PLUGIN -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/lib64/qt-3.3/mkspecs/default -I. -I/usr/local/include -I/usr/local/include -I/usr/include -I/usr/lib64/qt-3.3/include -o streamsui.o streamsui.cpp
streamsui.cpp:13:27: error: mythtv/compat.h: No such file or directory
streamsui.cpp: In member function ‘void StreamsUI::handleTreeListSelection(int, QValueVector<int>*)’:
streamsui.cpp:649: error: no matching function for call to ‘MythProgressDialog::MythProgressDialog(QString, int&, bool, StreamsUI* const, const char [17])’
/usr/local/include/mythtv/mythdialogs.h:196: note: candidates are: MythProgressDialog::MythProgressDialog(const QString&, int)
/usr/local/include/mythtv/mythdialogs.h:189: note:                 MythProgressDialog::MythProgressDialog(const MythProgressDialog&)
streamsui.cpp:732: error: no matching function for call to ‘MythProgressDialog::MythProgressDialog(QString, int&, bool, StreamsUI* const, const char [17])’
/usr/local/include/mythtv/mythdialogs.h:196: note: candidates are: MythProgressDialog::MythProgressDialog(const QString&, int)
/usr/local/include/mythtv/mythdialogs.h:189: note:                 MythProgressDialog::MythProgressDialog(const MythProgressDialog&)
streamsui.cpp:825: error: no matching function for call to ‘MythProgressDialog::MythProgressDialog(QString, int&, bool, StreamsUI* const, const char [17])’
/usr/local/include/mythtv/mythdialogs.h:196: note: candidates are: MythProgressDialog::MythProgressDialog(const QString&, int)
/usr/local/include/mythtv/mythdialogs.h:189: note:                 MythProgressDialog::MythProgressDialog(const MythProgressDialog&)
streamsui.cpp:960: error: no matching function for call to ‘MythProgressDialog::MythProgressDialog(QString, int&, bool, StreamsUI* const, const char [17])’
/usr/local/include/mythtv/mythdialogs.h:196: note: candidates are: MythProgressDialog::MythProgressDialog(const QString&, int)
/usr/local/include/mythtv/mythdialogs.h:189: note:                 MythProgressDialog::MythProgressDialog(const MythProgressDialog&)
streamsui.cpp: In member function ‘void StreamsUI::playVideo(const QString&, const QString&, const QString&)’:
streamsui.cpp:1349: error: ‘class MythContext’ has no member named ‘sendPlaybackStart’
streamsui.cpp:1365: error: ‘class MythContext’ has no member named ‘sendPlaybackEnd’
make[1]: *** [streamsui.o] Error 1
make[1]: Leaving directory `/opt/Software/mythtv_svn/mythplugins/mythvodka/mythvodka'
make: *** [sub-mythvodka] Error 2


It seems I need compat.h, though I'm not sure where that comes from as it's not in my libraries anywhere.  Also, this is a 64bit install.

Thanks!

---

### Post by Spookster on 2009-02-13
My mythfrontend crashes when I try to open MythVodka. The last message is:

2009-02-13 22:02:50.744 Error parsing data from grabber: Error: unexpected end of file Location Line: 1 Column 1

Any suggestions appreciated!

(Running the latest MythVodka package from the PPA, on mythbuntu intrepid).

---

### Post by iitywygms on 2009-02-14
> **Spookster said:**
> My mythfrontend crashes when I try to open MythVodka. The last message is:

2009-02-13 22:02:50.744 Error parsing data from grabber: Error: unexpected end of file Location Line: 1 Column 1

Any suggestions appreciated!

(Running the latest MythVodka package from the PPA, on mythbuntu intrepid).

see post [#157]("http://ubuntuforums.org/showpost.php?p=6623330&postcount=157")

---

### Post by Spookster on 2009-02-15
Thanks!!! Searched the thread, but missed that. I don't plan to use hulu so didn't think I needed it.

Should the mythvodka-hulu-generator package be a dependency of mythvodka?

---

### Post by jdeslip on 2009-02-15
One thing I find annoying with mythvodka is that, since hulu has a lot of shows, it takes forever (like a minute) to scroll down to ones that start with Z.  Is there a way to change the streams-ui.xml file to have speeded up scrolling like mythmusic has or to allow scrolling up from the top of the list bring you to the bottom??

---

### Post by jdeslip on 2009-02-15
Ok.  I found how to set the PageUP/DOWN universal keybind.  This drastically helps out.

---

### Post by iitywygms on 2009-02-16
> **jdeslip said:**
> Ok.  I found how to set the PageUP/DOWN universal keybind.  This drastically helps out.

Please share how to do this.
Never mind.  I figured this out.

---

### Post by jdeslip on 2009-02-16
> **iitywygms said:**
> Please share how to do this.
Never mind.  I figured this out.

Well, in case anyone else is out there wanting to know:

Go to "Utilities/Setup" -> "Edit Keys" -> "Global" -> Then Set Page Up and Page Down to Be Some Button On Your Remote

Additionally, you might want to set a repeat value of 1 to these buttons so you can hold them down to scroll faster.  I set these to channel up and channel down.  Here is my lircrc for those buttons:

begin
prog = mythtv
button = ChanUp
config = Alt+Up
repeat = 1
delay = 1
end

begin
prog = mythtv
button = ChanDown
config = Alt+Down
repeat = 1
delay = 1
end

---

### Post by OldThrashbarg on 2009-02-17
> **scary_jeff said:**
> Just been having another go at getting this working. I refreshed /var/tmp while trying to watch a stream:
During the initial buffering, iplayerdump.partial.mov steadily increases in size. When the buffering finishes, stream.mpg is created, and rapidly reaches a size of 10 megs or so. The mov file carries on getting bigger. If I pause the playback, the partial file will carry on getting bigger and bigger, but even after leaving it for 5 minutes (by which time the partial file is over 50 megabytes), the stream.mpg never changes size, and I can't watch past the first 30 seconds or so having unpaused. It just doesn't seem to be doing anything with the data that it downloads after the initial buffering stage.
Is stream.mpg even the file I'm watching?

I'm having a similar problem, although with me it loads more generally, but still not the whole show. It's slightly different though, with both iplayerdump.partial.mov and stream.mpg stopping before the show has finished downloading, but at different times. For example, with one hour long program, stream.mpg loads around 27 minutes worth (250ish MB) of it quickly and then just stops, whilst iplayerdump.partial.mov loads around 80MB but will play all that has been loaded by stream.mpg. The internet connection is plenty quick enough to load the program much faster than it takes to play, but it reaches a certain point and then stops. This is for iPlayer streams.

---

### Post by Neon Dusk on 2009-02-17
Are you using the internal player or mplayer?

---

### Post by rmotters on 2009-02-17
OK, I do not use Ubuntu, but I use Mythdora and I am trying to get mythvodka implemented. 

I am in the UK, so I am most interested in  BBC iPlayer and possibly ITV stuff (as supported by the latest release of get_iplayer).

I have had limited success in getting the BBC iPlayer stuff working, I think there is a bug introduced in the latest version which does not like mythvodka. I am going to look further into this.

I am wondering why mythvodka is streaming the iplayer stuff down to a file and running mencoder on it (though playiplayer.sh). When you can just pipe it into a configured player. For instance, if you run the command:

> get_iplayer --stdout --get ????????.mov | mplayer -cache 3072 -

This streams directly into mplayer (which should work the same as mencoder, cause they are built from the same code base). I tried this last night and I was pleasantly surprised at how good this actually works. 

Also if you want to use mencoder you pipe directly into that.

Lastly, the mythvodka GUI doesn't seem to allow for multiple programmes inside the same series.

Anyway keep up the good work and I am looking forward to v08.

---

### Post by azmyth on 2009-02-17
I just installed this on my mythbuntu system with the package from tgm4883. I'm running AMD 64bit and the rtmpdump in the deb package didn't work since it complained about libboost_regex. I ended up downloading the rtmpdump tar file and just did a make to create my own rtmpdump executable. Just posting to let other people know.

Does anyone know if there is a hulu grabber that fixes the occasional bad url. For example, the Sugar Bowl points to a King of the Hill episode.

---

### Post by OldThrashbarg on 2009-02-17
> **Neon Dusk said:**
> Are you using the internal player or mplayer?

I was using mplayer. Switching to the internal seems to have solved it though. Thanks for the pointer.

---

### Post by jdeslip on 2009-02-17
How do you get it to use the internal player?  MythVodka always uses mplayer for me (at least on the hulu programs).  Internal is selected for all the "File Types" in the settings, though.

---

### Post by jdeslip on 2009-02-17
ok... so, for hulu at least, the downloaded file is never encoded to mpg.  It is actually just played as a .mov.  Why this is done, I don't know.   

streamsui.cpp calls /usr/bin/hulu which creates the .mov but doesn't ever do any encoding with mencoder.  /usr/bin/playhulu.sh is never actually used as far as I can tell.  

I think it would be worth it to modify streamsui.cpp to call playhulu.sh instead of /usr/bin/hulu so that we can create streams.mpg file.  This has the benefit of allowing us to use the internal player and vdpau and not letting us jump past the end of the streams.mpg file.  In mplayer you can easily jump forward and end up out of the file...

Do you think you can make this change in your package tgm4883?

---

### Post by jdeslip on 2009-02-17
To accomplish this I think you just need to make the following change 

   if(m.type == "hulu")
    {
    // Start downloading

        QString curl = gContext->GetSetting("MythVodka.Grabber");
        QString mencoder = gContext->GetSetting("MythVodka.Encoder");
        QString filename = "/var/tmp/iplayerdump.partial.mov";
        QString get_iplayer = gContext->GetSetting("MythVodka.GetIplayer");

        QStringList args ;
        args += "/usr/bin/hulu";
        args += m.streamUrl ;
        args += filename ;

to

    if(m.type == "hulu")
    {
    // Start downloading

        QString curl = gContext->GetSetting("MythVodka.Grabber");
        QString mencoder = gContext->GetSetting("MythVodka.Encoder");
        QString filename = "/var/tmp/stream.mpg";
        QString get_iplayer = gContext->GetSetting("MythVodka.GetIplayer");

        QStringList args ;
        args += "/usr/bin/playhulu.sh";
        args += curl ;
        args += mencoder ;
        args += m.streamUrl ;

This, I think, involves waiting for the entire file to be dumped/downloaded before running mencoder on it - which probably takes a long time.  I am guessing  this is why the original author had it just play the .mov directly instead of encoding it.  So, maybe it is not actually worth implementing...

---

### Post by jdeslip on 2009-02-17
sorry to keep spamming this thread.  But, I think the code change I suggested above will work just fine.  I see in the playhulu.sh that we start the download sleep for 10 seconds, then start encoding it.  As long as the encoding isn't faster than the download, I guess it should work...  Can you test this out in your package, tgm4883?

---

### Post by tgm4883 on 2009-02-18
> **jdeslip said:**
> sorry to keep spamming this thread.  But, I think the code change I suggested above will work just fine.  I see in the playhulu.sh that we start the download sleep for 10 seconds, then start encoding it.  As long as the encoding isn't faster than the download, I guess it should work...  Can you test this out in your package, tgm4883?

Well i've done some other testing on that and encoding is definitly faster than downloading.  This causes major issues and unless someone can find a way to either A) make it so that mencoder will pause encoding if the buffer runs out, or B) make it easily configureable to encode or not, I can't put that in the package.

I'm working on some other stuff to work with hulu because I don't really like the way mythvodka works.  So unless browsing the hulu site with mythvodka gets alot faster I probably won't be messing with these packages.  If anyone would like to take over the packaging and put this on their own PPA go right ahead.

---

### Post by jdeslip on 2009-02-18
Ah, fair enough.  I worried that encoding would be faster.  I will play around really quickly to see if I can find a way to prevent mencoder from reaching the end of the file.  I won't try too hard, though.

I hope you are successful in coming up with a new hulu plugin.  That would be quite nice.  Vodka more or less works, but it isn't very elegant or fast.

---

### Post by jdeslip on 2009-02-18
Well, I thought I could do something like what rmotters suggested which is pipe the output of rtmpdump right into mencoder.  Unfortunately, only the get_iplayer command has the --stdout option, rtmpdump and get_hulu does not...

---

### Post by OldThrashbarg on 2009-02-18
> **jdeslip said:**
> How do you get it to use the internal player?  MythVodka always uses mplayer for me (at least on the hulu programs).  Internal is selected for all the "File Types" in the settings, though.

I'm not sure on the exact menu structure as I've altered mine a fair bit, but it'll be something like Media Settings -> Videos Settings -> Player Settings and change Default Video Player to Internal.

---

### Post by jdeslip on 2009-02-18
Ya, that works.  Unfortunatley, the internal player sucks for player the .mov files that the vodka hulu plugin generates.  I still can't find a good way to encode them to mpg as they download...

---

### Post by jdeslip on 2009-02-18
Now, it looks like the hulu plugin does not work at all.  

Every single file says: "Error: this file is not available for streaming."  It seems hulu has changed something on their site that broke vodka.

The XBMC guys are reporting the same problem here: [http://xbmc.org/forum/showthread.php?t=42041&page=54](http://xbmc.org/forum/showthread.php?t=42041&page=54)

Looks like rtmpdump is broken for hulu.

---

### Post by jdaddin on 2009-02-18
MythVodka not working seems to be related to the fact that Hulu pulled all of their videos from TV.com.  It seems to have happened at the exact same time so I'm sure it's no coincidence.  Perhaps TV.com was indirectly using those links to view the videos on their site.  If I manually go this URL for example : 

[http://releasegeo.hulu.com/content.select?pid=6b3f69b50a4fcb7753dde5173721103ecad511a7da87a4e5d9af4a3ec9fccf17~569d7557db970fc1c424406cdc30203aafbf7bf22e7a460719cf8a470eac0901&mbr=true&format=smil]("http://releasegeo.hulu.com/content.select?pid=6b3f69b50a4fcb7753dde5173721103ecad511a7da87a4e5d9af4a3ec9fccf17~569d7557db970fc1c424406cdc30203aafbf7bf22e7a460719cf8a470eac0901&mbr=true&format=smil")

This formerly working link now displays a page that says "Media is not available" .

---

### Post by jdeslip on 2009-02-18
[http://blog.boxee.tv/2009/02/18/the-hulu-situation/#disqus_thread](http://blog.boxee.tv/2009/02/18/the-hulu-situation/#disqus_thread)

Hulu just blocked Boxee as well (which is basically just a browser with a flash plugin).  It seems hulu on your TV won't be happening again soon...

I guess the decision to disallow programs like MythVodka and XBMC came at a similar time as asking Boxee to remove their content.  

Sad days are here again...

---

### Post by iitywygms on 2009-02-18
Well this sucks.  After all the futzin around to get this to work. 
I am sad. :(
Any opinion as to why they did this?

---

### Post by nrune on 2009-02-18
Who knows...

What is the difference between using mythvod or boxee to display content and using vnc to openup firefox surf to hulu.com and display content that way? Either way content ends up on my tv from hulu.  One way is more trouble than the other. 

Mike

---

### Post by tazz4vr on 2009-02-18
My brother was just complaining about this to me...here is a copy of what he sent...it is from Jason Kilar's blog...bummer days man!

Doing hard things
February 18th, 2009

"I always like to look on the optimistic side of life, but I am realistic enough to know that life is a complex matter." — Walt Disney

Later this week, Hulu's content will no longer be available through Boxee. While we never had a formal relationship with Boxee, we are under no illusions about the likely Boxee user response from this move. This has weighed heavily on the Hulu team, and we know it will weigh even more so on Boxee users.

Our content providers requested that we turn off access to our content via the Boxee product, and we are respecting their wishes. While we stubbornly believe in this brave new world of media convergence — bumps and all — we are also steadfast in our belief that the best way to achieve our ambitious, never-ending mission of making media easier for users is to work hand in hand with content owners. Without their content, none of what Hulu does would be possible, including providing you content via Hulu.com and our many distribution partner websites.

Our mission to make media dramatically easier and more user-focused has not changed and will not change. We will not stop until we achieve it and we are sober in our assessment that we have such a long way to go.

The maddening part of writing this blog entry is that we realize that there is no immediate win here for users. Please know that we take very seriously our role of representing users such that we are able to provide more and more content in more and more ways over time. We embrace this activity in ways that respect content owners' — and even the entire industry's — challenges to create great content that users love. Yes, it's a complex matter. A tough mission, and a never-ending one, but one we are passionately committed to.

For those Boxee users reading this post, we understand and appreciate that you're likely to tell us that we're nuts. Please know that we do share the same interests and won't stop innovating in support of the bigger mission.

---

### Post by ChiaGod on 2009-02-19
The post from the Hulu CEO is here:

[http://blog.hulu.com/2009/2/18/doing-hard-things#comments](http://blog.hulu.com/2009/2/18/doing-hard-things#comments)

There's more info on finding a workaround here:

[http://xbmc.org/forum/showthread.php?t=42041&page=54](http://xbmc.org/forum/showthread.php?t=42041&page=54)

User ptaylor had this to say:
"Ok - Here's what I've been able to verify so far. Using Wireshark, I've traced a browser session, to watch the same show that I was able to pull down with rtmpdump yesterday. In my trace, I see the request going for the original PID that I saw yesterday. I hard-coded that pid into the get_hulu.pl file, and I pulled down that entire show just fine.

So, rtmpdump isn't broken - it still works just fine, as long as you have the right pid. I think the player.swf file has been updated so that it performs some sort of calculation to get the real pid from the "encrypted pid". That explains why no one is complaining about this on the boxee forum, as I think they use the player.swf file to actually play the content."

---

### Post by ChiaGod on 2009-02-19
Also, in case anybody was interested, here's how I got MythVodka working with Hulu support (until today).  Note that I got it working w/o having to compile anything or alter any configuration files thanks to the excellent builds provided earlier in this thread.  For anybody else that wants to try this method here are the steps I took:

1. Adding Repositories/Getting packages:

1.1 Went to:
[https://launchpad.net/~tgm4883/+archive/ppa/](https://launchpad.net/~tgm4883/+archive/ppa/)
and added Thomas' repository which corresponded with my Ubuntu version.
1.1.1 From the pulldown at the webpage titled: "Display sources.list entries for:" Selected "Intrepid"
1.1.2 Copied the first deb line "deb [http://ppa.launchpad.net/tgm4883/ppa/ubuntu](http://ppa.launchpad.net/tgm4883/ppa/ubuntu) intrepid main"
1.1.3  Went to System > Software Sources > Third Party Software (Tab)
1.1.4  Clicked on "Add"
1.1.5  Pasted the line I just copied  
1.1.6  Clicked on "Add Source"
1.1.7  Updated my Software sources

1.2 Manually Downloaded the following file (couldn't find it on any repository):
[http://bazaar.launchpad.net/%7Etgm4883/%2Bjunk/hulu-xml-maker/download/head%3A/huluxmlmaker.cron.da-20090120223955-fws7phl67vcq7xvp-7/hulu-xml-maker.cron.daily](http://bazaar.launchpad.net/%7Etgm4883/%2Bjunk/hulu-xml-maker/download/head%3A/huluxmlmaker.cron.da-20090120223955-fws7phl67vcq7xvp-7/hulu-xml-maker.cron.daily)

2. Install the software:

2.1 Installed the Myth Vodka Package:
2.1.1 Open a terminal
2.1.1 Type: sudo apt-get install mythvodka
2.1.2 During the install, when it asks for the password I just pressed enter.
2.1.3 Install should complete without error

2.2 Installed Rtmpdump
2.2.1 sudo apt-get install rtmpdump

3 Setting up the hulu cron job (and running it for the first time)
3.1 Copy the cron job file to the cron directory
3.1.1 Open  terminal 
3.1.2 Navigate to where you downloaded the hulu-xml-maker.cron.daily file (ex: cd ~/Desktop/  OR  cd ~/Downloads )
3.1.3 Type: cp hulu-xml-maker.cron.daily /etc/cron.daily/hulu-xml-maker
3.2  Run the cron job manually for the first time
3.2.1 sudo /etc/cron.daily/hulu-xml-maker

4.  Re-launch MythTV and go to Media Library > Myth Vodka

Hope this helps somebody.  I may have made an error above (if so let me know and I'll be happy to correct it).  

Here's hoping that rtmpdump can be fixed to work with the changes Hulu has done.  With MythVodka + rtmpdump I finally had a way to get flash videos to play full screen (at 1920x1080) w/o the choppiness I was getting when using flashplayer within firefox.  Even with Flashplayer quality set to "low" and videos playing at 360p it still was noticeably jerky.  480p hulu videos through firefox + fullscreen was unwatchable.

Note that this is on a puny Sempron 2800+ system with an nVidia 8500 card.  The same rig can play 720p videos just fine (with the rare slowdown) and worked perfectly with Mythvodka.

---

### Post by vv1gg1 on 2009-02-19
so... can someone in the states try and access this and reply with the response

[http://releasegeo.hulu.com/content.select?pid=9ykTPNO9SLCb2j7VshdrSAnJAY84jDAD&mbr=true&format=smil](http://releasegeo.hulu.com/content.select?pid=9ykTPNO9SLCb2j7VshdrSAnJAY84jDAD&mbr=true&format=smil)

as long as that still gives us some xml with the streams in then were golden

---

### Post by vv1gg1 on 2009-02-19
actually that wont work. if anyone can confirm if they visit this page:

[http://www.hulu.com/watch/50454/nbc-nightly-news-with-brian-williams-bristol-palin-gives-birth-to-son](http://www.hulu.com/watch/50454/nbc-nightly-news-with-brian-williams-bristol-palin-gives-birth-to-son)

then after it plays visit:

[http://releasegeo.hulu.com/content.select?pid=9ykTPNO9SLCb2j7VshdrSAnJAY84jDAD&mbr=true&format=smil](http://releasegeo.hulu.com/content.select?pid=9ykTPNO9SLCb2j7VshdrSAnJAY84jDAD&mbr=true&format=smil)

and confirm that it then gives out some content

---

### Post by august495 on 2009-02-19
I get an "access to this content has expired"

---

### Post by tgm4883 on 2009-02-19
> **vv1gg1 said:**
> actually that wont work. if anyone can confirm if they visit this page:

[http://www.hulu.com/watch/50454/nbc-nightly-news-with-brian-williams-bristol-palin-gives-birth-to-son](http://www.hulu.com/watch/50454/nbc-nightly-news-with-brian-williams-bristol-palin-gives-birth-to-son)

then after it plays visit:

[http://releasegeo.hulu.com/content.select?pid=9ykTPNO9SLCb2j7VshdrSAnJAY84jDAD&mbr=true&format=smil](http://releasegeo.hulu.com/content.select?pid=9ykTPNO9SLCb2j7VshdrSAnJAY84jDAD&mbr=true&format=smil)

and confirm that it then gives out some content

Neither of those pages give me any content

---

### Post by tgm4883 on 2009-02-19
> **ChiaGod said:**
> 
1.2 Manually Downloaded the following file (couldn't find it on any repository):
[http://bazaar.launchpad.net/%7Etgm4883/%2Bjunk/hulu-xml-maker/download/head%3A/huluxmlmaker.cron.da-20090120223955-fws7phl67vcq7xvp-7/hulu-xml-maker.cron.daily](http://bazaar.launchpad.net/%7Etgm4883/%2Bjunk/hulu-xml-maker/download/head%3A/huluxmlmaker.cron.da-20090120223955-fws7phl67vcq7xvp-7/hulu-xml-maker.cron.daily)


You couldn't find that file because you need to install mythvodka-hulu-generator instead.  It does the same thing, but it was renamed.  It's on the repo.

With that being said, I'm still looking for someone to take over hosting the packaging.  I'm going to be doing some other mythtv related stuff on my ppa so if you keep using mine you may end up with a broken system.  Just download the source off my ppa and upload it to yours.

:EDIT:

And let me know so I can remove mythvodka

---

### Post by Seakip18 on 2009-02-19
The first link gives me a "This video is no longer available." 

Second one does not work as well. 


Dang it. I've been following this thread, hoping to give MythVodka a shot when I upgrade to 8.04 and migrate to a new machine. 

Thank you so much for the work y'all have done.

---

### Post by jdeslip on 2009-02-19
vv1gg1 - ya, neither of those play.  But, it may just be because that video is old (Dec 29) and removed from hulu altogether.  Perhaps try with a different video?

---

### Post by modorf on 2009-02-19
> **tgm4883 said:**
> Neither of those pages give me any content

I just got these links today, SNL Digital Short: Natalie Raps:

[http://www.hulu.com/watch/1404/saturday-night-live-snl-digital-short-natalie-raps](http://www.hulu.com/watch/1404/saturday-night-live-snl-digital-short-natalie-raps)

[http://releasegeo.hulu.com/content.select?pid=zm82gyqGADWi-WLdGJ1xIcinPl7rp9cT&mbr=true&format=smil](http://releasegeo.hulu.com/content.select?pid=zm82gyqGADWi-WLdGJ1xIcinPl7rp9cT&mbr=true&format=smil)

I got the link to releasegeo.hulu.com by watching my firewall traffic after starting the flash player.

---

### Post by jdeslip on 2009-02-19
the first link works.  the second tries to open something up in totem of type rtmp but totem says doesn't have codec...

---

### Post by modorf on 2009-02-19
> **jdeslip said:**
> the first link works.  the second tries to open something up in totem of type rtmp but totem says doesn't have codec...

I should have explained what I was posting.

The first link is hulu's main interface to a video clip.  The one I picked was an SNL Digital Short.
The second link is the rtmp playlist file that the flash player downloads before showing you the video.  I also attached it to allow for archiving.  An earlier posting by vv1gg1, posted links for an expired clip.  I was trying to help with a working clip.

I guess now we need to a) see if the file I posted will work for 'rtmpdump' and b) how to get this file in the future for other videos.

---

### Post by vv1gg1 on 2009-02-19
cheers modorf

this is only a temporary issue, as PIDs are static we can either script something to visit all pages in a browser and grab PIDs from proxy/http packt capturing. its ugly and slow but would make it hard for hulu to block, even if they change the algorithms on the encrypted PID the browser would always give us the real one

less ugly but more easily fixable by hulu is to use the good work of the xbmc guys to properly decrypt the PIDs. they cant use there work yet as they dont have a way of getting flash running from command line on xbmc (yet) but we can use gnash

---

### Post by jdeslip on 2009-02-19
Here is a thought:

Why don't make new plugin that uses the hulu xml generator and interface from vodka but just launches a fullscreen firefox or some lighter weight browser like epiphany...

---

### Post by modorf on 2009-02-19
vv1gg1:

do you know how MythVodka was grabbing the pid's before?
Was that something that Hulu was giving out freely?

---

### Post by jdeslip on 2009-02-19
I got hulu working through the mythbrowser plugin.  Just bookmarked the links to a bunch of shows.  Works pretty well.  Took a bit of finagling to get flash to work on the mythbrowser though.  I posted some instructions here:

[http://ubuntuforums.org/showthread.php?t=715604&page=2](http://ubuntuforums.org/showthread.php?t=715604&page=2)

The performance isn't anywhere near as good as vodka was, because I am actually playing the streams.  However, since this is just playing it in a webbrowser, there isn't much Hulu can do to kill it...

I am going to try to write a new plugin integrating mythbrowser that basically makes this a bit more seemless.

---

### Post by ghuber on 2009-02-20
The XBMC guys have already put a fix in place for Hulu.  Any chance this can be used to get it back on Mythbuntu?

[http://xbmc.org/forum/showthread.php?t=42041&page=59](http://xbmc.org/forum/showthread.php?t=42041&page=59)

---

### Post by azmyth on 2009-02-20
It works. Just make the changes to your /usr/bin/hulu and add the two files in the fix to your /usr/bin directory. Assuming you installed the ppa mythvodka package.

---

### Post by vv1gg1 on 2009-02-20
yeah someone has already done one version

[http://knoppmyth.net/phpBB2/viewtopic.php?p=119624#119624](http://knoppmyth.net/phpBB2/viewtopic.php?p=119624#119624)

---

### Post by jdeslip on 2009-02-20
Nevermind...

---

### Post by vv1gg1 on 2009-02-20
yeah, use this:

[http://xbmc.org/trac/attachment/ticket/5941/hulu_decrypt.diff](http://xbmc.org/trac/attachment/ticket/5941/hulu_decrypt.diff)

its 2 new files porting over the decrypt, importing those into hulu script and calling the decrypt method

porting over the code from the xbmc guys in the first place instead of rewriting is really paying off :p

---

### Post by tazz4vr on 2009-02-20
> **vv1gg1 said:**
> yeah, use this:

[http://xbmc.org/trac/attachment/ticket/5941/hulu_decrypt.diff](http://xbmc.org/trac/attachment/ticket/5941/hulu_decrypt.diff)

its 2 new files porting over the decrypt, importing those into hulu script and calling the decrypt method

porting over the code from the xbmc guys in the first place instead of rewriting is really paying off :p

After reading the above, I was like, huh?  Can you draw me pic's...lol... however my brother, who has since joined the forum I believe due to this whole issue and the way everyone in this thread has handled it and is trying to resolve the matter, great job...in any case, he remarked, with Oh Yeah, I see I see...I am going to assume this will make his livingroom/office off limits tonight as he tries to do whatever it is he is suppose to do....Sorry Kim!

---

### Post by bcg30506 on 2009-02-20
> **vv1gg1 said:**
> yeah, use this:

[http://xbmc.org/trac/attachment/ticket/5941/hulu_decrypt.diff](http://xbmc.org/trac/attachment/ticket/5941/hulu_decrypt.diff)

its 2 new files porting over the decrypt, importing those into hulu script and calling the decrypt method

porting over the code from the xbmc guys in the first place instead of rewriting is really paying off :p

I got this working and now most videos work again.  I've attached a tar file containing my new hulu script and the 2 new import dependencies.  Place all 3 of these into /usr/local/bin.  The only issue is WKRP "Turkeys Away" still does not play.  It does play within Firefox however.

---

### Post by nrune on 2009-02-21
Accoding to boxee and XBMC forums the hulu have changes around the crypto on the PID, so we are waiting on another hack.  This is usless, there is no way that Hulu can keep encrypting the PID and win.  So will content providers pull out of Hulu because it can not "protect" their content? 

Mike

---

### Post by vv1gg1 on 2009-02-21
its cool, the xbmc guys stumbled on the propper answer, use this:

[https://launchpad.net/pyswfdec/](https://launchpad.net/pyswfdec/)

to load the actual hulu flash/actionscript code that decrypts the PID. so every time you play a movie / update listings it pulls down the latest sec.swf and uses that to download the PID. then it would take a significant change for hulu to fix it.

or alternatively we do my first suggestion and the listings grabbed launches a real web browser and the PID is grabbed either through browser pulign, proxy or packet sniffing.

both these methods are feasible and would mean Hulu wouldnt be able to use simple changes of PID to hide video. this is all fixable, but its going to be back to me coding (or one of the people whos messaged me recently), these solutions arnt viable on the xbox due to dependancies. well everything is viable but it would be a ball ache for the xbmc guys.

but i prob wont release this in MythVodka or to the public, they dont want us to have the video so im not going to release anything to piss them off. but if there serious about stopping people they need to encrypt the video and not the PIDs... this is a quick fix to kick everyone off, and theyve proved that they can change the PIDs quicker than we can decrypt the algorithm. we have to use there own code, sec.swf, then we buy some more time.

theyre only pissing around atm, clearly spending more on laywers than techies :D

---

### Post by rmotters on 2009-03-03
Hi, again.

I have been looking at the mythvodka repository [http://code.google.com/p/mythvodka/](http://code.google.com/p/mythvodka/) and I noticed that the code as moved onto Mythtv 0.22 and QT4.

I have been spending some time trying to get the latest changes compatible with Mythdora, which is running MythTV 0.21 and hence QT3.

I understand that Mythbuntu is still using MythTV 0.21, so is there anybody here working and trying to do the same thing.

---

### Post by azmyth on 2009-03-03
The original package compiles under 0.21 which runs qt3. You had to make a few changes depending on the architecture but there's a link in this thread to the wiki that explains how to fix any issues on compile. The only problem is the original package won't work since the pids are now encrypted. There's a fix where you can use swfdec after compiling a small actionscript file with mtasc.

---

### Post by rmotters on 2009-03-04
I have the original version working and compiled. Being in the UK it more the latest iplayer functionality I am interesting in.

There looks like quite a dramatic improvement in this area, but I am struggling getting it working under 0.21

---

### Post by azmyth on 2009-03-04
When you say not working, what do you mean? Can you see the menus and you just can't get the iplayer to grab the show. You also need to install rtmpdump which will require some boost dependencies to compile rtmpdump.

---

### Post by rmotters on 2009-03-05
As I said I have the original (mythvodka.07.tar.gz) code compiled, working and a rpmbuilt. Everything is fine here (get_iplayer and rtmpdump is all working).

I want to run the latest SVN release (**r12**) of the mythvodka code from the google code repository ([http://code.google.com/p/mythvodka/](http://code.google.com/p/mythvodka/)). I having difficulties in getting this code compiled.

Since **r5**and **r6** the code has been written for mythtv 0.22 and QT4. I do not want to run mythtv 0.22 on my PVR, at the moment, so I trying to backport the latest release to mythtv 0.21 and Qt3. 

I was just wondering if there is anybody else out there trying to do a similar thing.

---

### Post by scary_jeff on 2009-03-05
> **rmotters said:**
> As I said I have the original (mythvodka.07.tar.gz) code compiled, working and a rpmbuilt. Everything is fine here (get_iplayer and rtmpdump is all working).

Do you have iplayer content working in the mythvodka gui? If so, would it be possible for me to get your rpm? I still haven't got iplayer working from within mythvodka, so it would be great to try a build that is proven to work with iplayer (most people here seem to be using hulu). I'm assuming it's a 32 bit build and I would be using alien to install it on ubuntu.

---

### Post by iitywygms on 2009-03-09
Another alternative?

[http://blog.boxee.tv/2009/03/06/new-version-hulu-update/](http://blog.boxee.tv/2009/03/06/new-version-hulu-update/)

---

### Post by davidstoll on 2009-03-12
Where exactly can I get hulu-xml-maker.cron.daily?

The link in this thread doesn't work for me.

Thanks!

*edit*

ok...
sudo apt-get install mythvodka-hulu-generator

So, now when I run the script cron.daily, it asks for a password.  My sudo password doesn't work.  Any ideas?

---

### Post by abstraktion on 2009-03-12
Have you tried running sudo /etc/cron.daily/mythvodka-hulu-generator?

eric

---

### Post by davidstoll on 2009-03-12
> **abstraktion said:**
> Have you tried running sudo /etc/cron.daily/mythvodka-hulu-generator?

eric

yes.

If I put sudo in front, as you suggest, it asks for my sudo password, which it accepts, and then it asks for another password.

The script has "su" command it in.  It should not have su or sudo commands in a cron job because you tell the crontab what credentials to use.

If it runs something that needs a password, it won't run because it is running in the background.  How would you enter a password in a cron job?  As far as I know, it would just timout and fail.

I think it needs to be edited to work with ubuntu correctly.

I'm going to remove all the "su mythtv -c" entries and see how that goes.  However, I'm a linux newbie, so I don't really know exactly what I'm doing.

Maybe I don't have the correct scrip....?  Can someone post it here?  Or at least link to it?

Thanks!

---

### Post by abstraktion on 2009-03-12
What are the permissions on the file?
```
ls -l /etc/cron.daily/mythvodka-hulu-generator
```

Mine are
```
-rwxr-xr-x 1 root root 2268 2009-02-02 10:58 /etc/cron.daily/mythvodka-hulu-generator
```

eric

---

### Post by davidstoll on 2009-03-12
> **abstraktion said:**
> What are the permissions on the file?
```
ls -l /etc/cron.daily/mythvodka-hulu-generator
```

Mine are
```
-rwxr-xr-x 1 root root 2268 2009-02-02 10:58 /etc/cron.daily/mythvodka-hulu-generator
```

eric

Mine is also...
-rwxr-xr-x 1 root root 2088 2009-03-12 14:53 mythvodka-hulu-generator

Would it be possible for someone to just post their script?  Even a copy and paste, so we can point things out and discuss it?

Thanks

Here is mine
```

#!/bin/bash

## Get Starting Date/time
DATE=`date '+%R %m/%d/%Y'`

## Remove the old XML file
rm /tmp/hulu.xml

## Write info to log and generate new XML File
su mythtv -c "echo '***** Starting daily update on $DATE *****' >> /var/log/mythtv/mythvodka-hulu-generator.log"
su mythtv -c "echo '' >> /var/log/mythtv/mythvodka-hulu-generator.log"
su mythtv -c "gethulu.pl /tmp/hulu.xml >> /var/log/mythtv/mythvodka-hulu-generator.log 2>&1"
su mythtv -c "echo '' >> /var/log/mythtv/mythvodka-hulu-generator.log"

## Make sure XML file is valid, regenerate if not. (Up to 3 times)
STATUS=`tail -n 1 /tmp/hulu.xml`

# Set broken to 0 so we don't have an infinite loop
BROKEN=0

while [ "$STATUS" != "</Streams></Feed></MediaStreams>" ] && [ "$BROKEN" != "3" ]
do
  BROKEN=$(($BROKEN+1))
  su mythtv -c "echo '***** XML file invalid, regenerating *****' >> /var/log/mythtv/mythvodka-hulu-generator.log"
  rm /tmp/hulu.xml >> /var/log/mythtv/mythvodka-hulu-generator.log 2>&1
  DATE=`date '+%R %m/%d/%Y'`
  su mythtv -c "echo '***** Starting regeneration of XML file on $DATE, retry number $BROKEN *****' >> /var/log/mythtv/mythvodka-hulu-generator.log"
  su mythtv -c "gethulu.pl /tmp/hulu.xml >> /var/log/mythtv/mythvodka-hulu-generator.log 2>&1"
done


## Get ending date/time
DATE=`date '+%R %m/%d/%Y'`

if [ $BROKEN == "3" ]; then
  echo "************************************* >> /var/log/mythtv/mythvodka-hulu-generator.log"
  echo "***** ERROR: XML File is broken ***** >> /var/log/mythtv/mythvodka-hulu-generator.log"
  echo "************************************* >> /var/log/mythtv/mythvodka-hulu-generator.log"
else
  ## Write to log and copy valid XML file to backend web dir
  su mythtv -c "echo '***** XML file valid, copying to backend web dir *****' >> /var/log/mythtv/mythvodka-hulu-generator.log"
  su mythtv -c "echo '***** Moving hulu to public directory *****' >> /var/log/mythtv/mythvodka-hulu-generator.log"
  su mythtv -c "echo '' >> /var/log/mythtv/mythvodka-hulu-generator.log"
  mv /tmp/hulu.xml /var/www/ >> /var/log/mythtv/mythvodka-hulu-generator.log 2>&1
  su mythtv -c "echo '' >> /var/log/mythtv/mythvodka-hulu-generator.log"
  su mythtv -c "echo '***** Daily Update finished on $DATE *****' >> /var/log/mythtv/mythvodka-hulu-generator.log"
fi

```


However, I changed it to this...removing the "su mythtv -c" and the quotes...because I didn't know the password it was asking for...
```

#!/bin/bash

## Get Starting Date/time
DATE=`date '+%R %m/%d/%Y'`

## Remove the old XML file
rm /tmp/hulu.xml

## Write info to log and generate new XML File
echo '***** Starting daily update on $DATE *****' >> /var/log/mythtv/mythvodka-hulu-generator.log
echo '' >> /var/log/mythtv/mythvodka-hulu-generator.log
gethulu.pl /tmp/hulu.xml >> /var/log/mythtv/mythvodka-hulu-generator.log 2>&1
echo '' >> /var/log/mythtv/mythvodka-hulu-generator.log

## Make sure XML file is valid, regenerate if not. (Up to 3 times)
STATUS=`tail -n 1 /tmp/hulu.xml`

# Set broken to 0 so we don't have an infinite loop
BROKEN=0

while [ "$STATUS" != "</Streams></Feed></MediaStreams>" ] && [ "$BROKEN" != "3" ]
do
  BROKEN=$(($BROKEN+1))
  echo '***** XML file invalid, regenerating *****' >> /var/log/mythtv/mythvodka-hulu-generator.log
  rm /tmp/hulu.xml >> /var/log/mythtv/mythvodka-hulu-generator.log 2>&1
  DATE=`date '+%R %m/%d/%Y'`
  echo '***** Starting regeneration of XML file on $DATE, retry number $BROKEN *****' >> /var/log/mythtv/mythvodka-hulu-generator.log
  gethulu.pl /tmp/hulu.xml >> /var/log/mythtv/mythvodka-hulu-generator.log 2>&1
done


## Get ending date/time
DATE=`date '+%R %m/%d/%Y'`

if [ $BROKEN == "3" ]; then
  echo "************************************* >> /var/log/mythtv/mythvodka-hulu-generator.log"
  echo "***** ERROR: XML File is broken ***** >> /var/log/mythtv/mythvodka-hulu-generator.log"
  echo "************************************* >> /var/log/mythtv/mythvodka-hulu-generator.log"
else
  ## Write to log and copy valid XML file to backend web dir
  echo '***** XML file valid, copying to backend web dir *****' >> /var/log/mythtv/mythvodka-hulu-generator.log
  echo '***** Moving hulu to public directory *****' >> /var/log/mythtv/mythvodka-hulu-generator.log
  echo '' >> /var/log/mythtv/mythvodka-hulu-generator.log
  mv /tmp/hulu.xml /var/www/ >> /var/log/mythtv/mythvodka-hulu-generator.log 2>&1
  echo '' >> /var/log/mythtv/mythvodka-hulu-generator.log
  echo '***** Daily Update finished on $DATE *****' >> /var/log/mythtv/mythvodka-hulu-generator.log
fi

```

However, mythvodka still crashes my mythtv frontend.  I suspect it has something to do with the fact that it has not created an XML file yet...because I can't get the script to run.

---

### Post by abstraktion on 2009-03-12
Your file is the same as mine. What do you get when you type: sudo su mythtv? and: groups (username)?

eric

---

### Post by davidstoll on 2009-03-12
> **abstraktion said:**
> Your file is the same as mine. What do you get when you type: sudo su mythtv? and: groups (username)?

eric


If I do this...
```

xxxxx@MythTV:/$ sudo su mythtv
[sudo] password for xxxxx: 
$ 

```
It takes my sudo password and then it looks like a get a new prompt/session.


If I do this...
```

xxxxx@MythTV:/$ su mythtv
Password: 

```

and I don't know the password....which is what it does when I run the original script.

---

### Post by nrune on 2009-03-13
Having some issues with the Hulu Generator script.  
```
nrune@bed-front:~$ sudo ./hulugen.pl
./hulugen.pl: line 11: /var/log/mythtv/mythvodka-hulu-generator.log: Permission denied
Use of uninitialized value $_ in pattern match (m//) at /usr/local/bin/gethulu.pl line 114.
Use of uninitialized value $_ in pattern match (m//) at /usr/local/bin/gethulu.pl line 114.
Use of uninitialized value $_ in pattern match (m//) at /usr/local/bin/gethulu.pl line 114.
Use of uninitialized value $_ in pattern match (m//) at /usr/local/bin/gethulu.pl line 114.
Use of uninitialized value $_ in pattern match (m//) at /usr/local/bin/gethulu.pl line 114.
Use of uninitialized value $_ in pattern match (m//) at /usr/local/bin/gethulu.pl line 114.
Use of uninitialized value $_ in pattern match (m//) at /usr/local/bin/gethulu.pl line 114.
Use of uninitialized value $_ in pattern match (m//) at /usr/local/bin/gethulu.pl line 114.
Use of uninitialized value $_ in pattern match (m//) at /usr/local/bin/gethulu.pl line 114.
./hulugen.pl: line 27: syntax error near unexpected token `newline'
./hulugen.pl: line 27: `  echo '***** XML file invalid, regenerating *****' >> '

```

Mythvodka crashes on doing /bin/cat /tmp/hulu.xml. 

Help.

Thanks

---

### Post by davidstoll on 2009-03-13
> **nrune said:**
> Having some issues with the Hulu Generator script.  
```
nrune@bed-front:~$ sudo ./hulugen.pl
./hulugen.pl: line 11: /var/log/mythtv/mythvodka-hulu-generator.log: Permission denied
Use of uninitialized value $_ in pattern match (m//) at /usr/local/bin/gethulu.pl line 114.
Use of uninitialized value $_ in pattern match (m//) at /usr/local/bin/gethulu.pl line 114.
Use of uninitialized value $_ in pattern match (m//) at /usr/local/bin/gethulu.pl line 114.
Use of uninitialized value $_ in pattern match (m//) at /usr/local/bin/gethulu.pl line 114.
Use of uninitialized value $_ in pattern match (m//) at /usr/local/bin/gethulu.pl line 114.
Use of uninitialized value $_ in pattern match (m//) at /usr/local/bin/gethulu.pl line 114.
Use of uninitialized value $_ in pattern match (m//) at /usr/local/bin/gethulu.pl line 114.
Use of uninitialized value $_ in pattern match (m//) at /usr/local/bin/gethulu.pl line 114.
Use of uninitialized value $_ in pattern match (m//) at /usr/local/bin/gethulu.pl line 114.
./hulugen.pl: line 27: syntax error near unexpected token `newline'
./hulugen.pl: line 27: `  echo '***** XML file invalid, regenerating *****' >> '

```

Mythvodka crashes on doing /bin/cat /tmp/hulu.xml. 

Help.

Thanks


I'm having a similar issue.  I get a permission denied error.

---

### Post by nrune on 2009-03-13
Well it appears that the xml was actually generated, and was imported into mythvodka.  But every showing has the video is missing error message. 

Here is the first part of the xml

```
<MediaStreams>
<Feed><Name>21 Grams</Name><Provider>Hulu Movies</Provider><FeedImage>http://as$
<Stream>
<Name>21 Grams</Name>
<Url>http://www.hulu.com/watch/49352</Url>
<Subtitle></Subtitle>
<Synopsis>11/21/2003 - What is the weight of life?  Guilt?  Revenge?  Criticall$
<StreamImage>http://thumbnails.hulu.com/13/217/56037_145x80_generated__LQZ3VsuN$
</Stream>
</Streams></Feed><Feed><Name>Abel Raises Cain</Name><Provider>Hulu Movies</Prov$
<Stream>
<Name>Abel Raises Cain</Name>
<Url>http://www.hulu.com/watch/56337</Url>
<Subtitle></Subtitle>
<Synopsis>07/31/2008 - Filmmaker Jenny Abel explores the life and career of her$
<StreamImage>http://thumbnails.hulu.com/14/325/65600_145x80_generated__BC-cxksz$
</Stream>
</Streams></Feed><Feed><Name>Adios, Sabata</Name><Provider>Hulu Movies</Provide$
<Stream>

```

but nothing works, getting the video missing on everything.

Pasting the url in the xml file into a browser does work.  So I am not sure why it's not working.

---

### Post by BigZee on 2009-03-22
Hi,

I'm not sure how many BBC iplayer users there are out there but if there are any, and they have BBC iplayer working with mythvodka, them I'd appreciate some help. After one or two problems that I managed to solve, I've finally got to this point :-

2009-03-22 19:12:54.390 MythVodka Data Grabber: Executing '/usr/local/bin/get_iplayer -q --mythtv - --xml-channels'
2009-03-22 19:12:55.524 Grabber Finished. Processing Data.
2009-03-22 19:12:55.559 Error parsing data from grabber: Error: unexpected end of file Location Line: 5945 Column 1

By this stage, it seems to have successfully downloaded the data from iplayer but clearly is not expecting the end of file. No idea what the problem is but my installation seems to be ok.

---

### Post by Keithamus on 2009-04-05
I'd like some help with the BBC iplayer too.

I followed the guide on [http://nevillehome.co.uk/dokuwiki/doku.php?id=mythbuntu:bbc_iplayer_mythvokda](http://nevillehome.co.uk/dokuwiki/doku.php?id=mythbuntu:bbc_iplayer_mythvokda) but all I get is the rude messages, I can't seem to ever do anything with it!

The same goes for the rest of the streams actually, get the "sorry bean" message for the majority of them.

---

### Post by azmyth on 2009-04-05
The hulu part is busted and you have to be in the UK for the BBC to work.

---

### Post by Keithamus on 2009-04-06
I am in the UK, and I deleted the reference to the hulu script in the settings gui.

---

### Post by jeffspen on 2009-04-07
I'm in UK and will not be using Hulu. But like Keithamus am getting a "sorry old bean..." message on all streams. If I run get_iplayer from terminal in my home folder as something like this:

get_iplayer --get 123 

123 being an arbitary number as a BBC programme reference, it downloads a programme fine. It's quite amusing seeing what you get by typing in random numbers. However this doesn't quite make up for the fact it doesn't function in mythtv!

Why is mythvodka not able to do the same?
Is it a permissions thing? 
I know the partial.mov file it creates should be stored in /var/tmp/
This folder is owned by root. I don't see the file appear and disappear at all.
I've tried running get_iplayer from within here in terminal with the script itself being owned by me and then by root and it works both times. 
Very confused...

I adjusted the streams-ui.xml for use in my blootube-wide theme if anyone wants a copy. Put it in /usr/share/mythtv/themes/default-wide/ 
And also a badly cobbled together watermark for it. Both things done to amuse myself while the damn thing doesn't work.

---

### Post by azmyth on 2009-04-07
What version of get_iplayer are you using? I think there's a newer one. I tried it but I can't get BBC feeds since I'm in the US.

---

### Post by maff on 2009-04-09
Got it all compiled after reading through this thread, but it wont initialise

mythfrontend gives

```
2009-04-09 19:32:39.582 MythPlugin::init() dlerror: /usr/lib/mythtv/plugins/libmythvodka.so: undefined symbol: _ZNK7Setting9classNameEv
2009-04-09 19:32:39.582 Unable to initialize plugin 'mythvodka'.

``` 

Any clues?

---

### Post by jeffspen on 2009-04-10
Was using 07.
Just found about 12 revisions on google code:

[URL="http://mythvodka.googlecode.com/svn/trunk/"]


 Might try them soon or wait for the tar of 08. There's a lot of files...

---

### Post by AlecJ on 2009-04-15
Got the get_iplayer part working, have made changes (on going) in streamsui.cpp and compiled it.

QStringList argsmov ;
        argsmov += get_iplayer ;
    argsmov += "-f" ;
    argsmov += "--force-download" ;
    argsmov += "--rtmp" ;
        argsmov += "-o" ;
        argsmov += [COLOR=Red]"/var/lib/mythtv/videos"[/COLOR] ;
        [COLOR=Red]//argsmov += "--file-prefix" ;
        //argsmov += "iplayerdump" ;[/COLOR]
        argsmov += "--get" ;
        argsmov += m.streamUrl ;
    
        QProcess procmov(argsmov);
        procmov.start();
    
        VERBOSE(VB_IMPORTANT, QString("Running Command: %1")
            .arg(argsmov.join(" ")));
    
    // Make a progress bar as big as the value for bufferSize
    
        int bufferSizemov = [COLOR=Red]500000[/COLOR] ;
    
        VERBOSE(VB_IMPORTANT, QString("Buffer Required: %1")
                    .arg(bufferSizemov)); 
    
        MythProgressDialog *buffer_progress;
        buffer_progress = new MythProgressDialog(
            QObject::tr("[COLOR=Red]Downloading from the BBC[/COLOR]"), bufferSizemov, true, this, SLOT(cancelPressed()));

This will download the chosen file to /var/lib/mythtv/videos which is a mythtv owned folder, it will not update the screen so you can not watch the download progress but will after the download has finished give the "sorry old bean" error. no matter you have the file.
Then in the frontend you need to set .mov files up so
Utilities / setup
Setup
Media Settings
Video Settings
File types

Now add the a new type mov and in the command box .    mplayer -fs -zoom %s   or similar.
I also added in the General :/var/lib/mythtv/videos   as I keep my films elsewhere.

This is ongoing cos it did'ent work out of the box for me.
looking to get the teletext working at some point ??

now there is ITV1 ****
[http://linuxcentre.net/getiplayer/](http://linuxcentre.net/getiplayer/)

---

### Post by slamduncan on 2009-04-17
scary_jeff I have the same problem as you. It's not that our internet connections are too slow. It's that our machines are faster. What happens is the transcoding done by mencoder executes faster than either the download or playback. When mencoder reaches the end of what's been downloaded so far it exits. The somewhat brute force solution I'm testing at the moment is to use the nice command to lower the priority of the mencoder process. You can try it for yourself by modifying /usr/local/bin/playiplayer.sh so that the exec line reads "exec nice -n 19 $MENCODER etc..". 19 is the lowest priority on a scale of -20 to 19 so some experimentation may be needed for your machine.

Does anyone have a suggestion for a better solution to this particular problem?

Seems to me that it might make sense to download and transcode in sequence rather than parallel then dump the output into the videos directory of Myth for later viewing...
D.

---

### Post by pau1mi11er on 2009-04-21
I'm having the same problems and found a solution - although not particularly fantastic one I suspect

1) Changed get_iplayer to populate the url XML field with the index number of the programme
2) Changed MythVodka to remove the --rmtp streaming method in the commandline it generates for get_iplayer
3) Changedthe buffer length (although I don't know whether this really is needed)

Once these had been done then it seems to work. This is with MythVodka07 - no changes to the published tar (apart from those above) and compiled into MythBuntu fixes 0.21 (followed nevilles compiliation instructions which seemed to work fine).

I've still got some problems with it (the listing index sometimes does not work (I choose a programme and something completely different pops up) and when browsing through the listings I get repeat entries for difference episodes of the same programme (I've got three instances of "All the small things" for example, all reporting episode 1 - probably are episode 1, 2 and 3 though)). I've had a quick look at revision3 and this seems to work - have not tried Hulu yet. What would be interesting is to get the ITV bit working as well - it is supported by get_iplayer, and the bbc radio player.

Any thoughts on the matter gratefully received.

Paul

---

### Post by AlecJ on 2009-04-24
Have stopped using Mythvodka now in favor of using the latest get_iplayer from the command line, there is full documentation here [http://linuxcentre.net/getiplayer/](http://linuxcentre.net/getiplayer/) and I can get the HD stuff and ITV, radio etc downloaded for later viewing in the videos folder with mplayer in mythtv.
Will return to mythvodka in the future when I have time to make it work. Hulu is only supported for download you can't decode it yet.

---

### Post by mikeglover on 2009-04-25
I have been trying to get MythVodka working on Mythbuntu 8.10 for about a week with little success.
After trying to install it using the Wiki instructions (which doesn't work) I used the deb package found at [http://archive.ubuntu.org.cn/ppa/tgm4883/ppa/ubuntu/pool/main/m/mythvodka/](http://archive.ubuntu.org.cn/ppa/tgm4883/ppa/ubuntu/pool/main/m/mythvodka/)

Revision3 content works fine, apart from audio delay but I'll work on that later.

BBC content is shown in the list but when I go to play any of them. I get the message 'Oh No! .... '

I have the latest version of get_iplayer (1.67) in /usr/local/bin (chmod +x) and lastest version of rtmpdump (1.4) in /usr/bin

get_iplayer and rtmpdump work from the command line as far as I can see.

Is anyone else able to view BBC content at the moment? Or know what I might be doing wrong?
This is starting to get on my nerves now!

---

### Post by pau1mi11er on 2009-04-27
What I found was exactly the same. When I looked in the mythfrontend.log I saw that the get_iplayer command string that was generated by mythvodka was not finding any files to download and thus there was nothing in the /var/tmp folder to then encode and view.

The problem was that the get_iplayer was trying to find a non-existant file called, for example, x43f35d.mov (I made that up) which was built from the streamurl xml entry that get_iplayer generates when it does an index. However, all that comes into the xml is the x43f35d - the .mov is added by mythvodka. I then tried that manually and nothing came up - but by removing the .mov, removing the requirement to stream by rtmp and populating the streamurl field in the xml file with the index then it seems to work (most of the time).

Myth vodka generates "...--get x43f34d.mov ...", and if x43f34d is program index 154 then "...--get 154 ..." works. a .mov file gets into the /var/tmp directory and is encoded and displayed correctly.

Not sure if this is the right thing to do - and it probably only gets a pretty low res thing but it is better than nothing!

---

### Post by mikeglover on 2009-04-27
> **pau1mi11er said:**
> What I found was exactly the same. When I looked in the mythfrontend.log I saw that the get_iplayer command string that was generated by mythvodka was not finding any files to download and thus there was nothing in the /var/tmp folder to then encode and view.

The problem was that the get_iplayer was trying to find a non-existant file called, for example, x43f35d.mov (I made that up) which was built from the streamurl xml entry that get_iplayer generates when it does an index. However, all that comes into the xml is the x43f35d - the .mov is added by mythvodka. I then tried that manually and nothing came up - but by removing the .mov, removing the requirement to stream by rtmp and populating the streamurl field in the xml file with the index then it seems to work (most of the time).

Myth vodka generates "...--get x43f34d.mov ...", and if x43f34d is program index 154 then "...--get 154 ..." works. a .mov file gets into the /var/tmp directory and is encoded and displayed correctly.

Not sure if this is the right thing to do - and it probably only gets a pretty low res thing but it is better than nothing!

What exactly do I need to do? Do you change get_iplayer or the streamurl xml?

---

### Post by mikeglover on 2009-04-27
After a bit of playing round trying to get this thing working. I am now getting the following error in the mythtv log. The frontend still complains saying "Oh No..."

```
2009-04-27 20:44:26.490 Running Command: /usr/local/bin/get_iplayer -f --force-download --rtmp -o /var/tmp --file-prefix iplayerdump --get b00k2ph9.mov
2009-04-27 20:44:26.491 Buffer Required: 300000
2009-04-27 20:44:29.770 Running Command: /usr/bin/playiplayer.sh /usr/bin/curl /usr/bin/mencoder b00k2ph9.mov
2009-04-27 20:44:29.770 Buffer Required: 3000000
2009-04-27 20:44:29.835 Selection: File: b00k2ph9.mov
2009-04-27 20:44:33.515 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-04-27 20:44:33.527 Using protocol version 40
2009-04-27 20:44:35.472 Deleting UPnP client...
```I feel i'm a bit closer, a iplayerdump.partial.avi.flv appears in the var/tmp folder and when I play this I get the program I selected. Quality is poor but better than nothing. But still it doesn't work in Mythtv.
Now running lastest get_iplayer (1.68 ) and rtmpdump (1.5)

Has anyone had this kind of error message or knows what might be happening?

---

### Post by vv1gg1 on 2009-04-27
hello yes yes the get_iplayer chap changed the code so it creates different file names. why the blast it couldnt just write to stdout or let the user specify a filename instead of it making up is... rant

anyway i started fixing it the other day, the beeb now do some nice high quality flash streams and even some HD streams so it just needs polishing up and ill drop the get_iplayer chap a message to get it a bit more futureproof

but actually im working my *** off atm on other stuff, and this weekend ill be at the reading beer festival so dont expect much productivity for a week or two.

if anyone wants to fix have a look at mythstreamsui.cpp and search for iplayer, all pretty basic.

---

### Post by jdeslip on 2009-04-27
Lets face it, mythvodka is at the best of times a buggy/ugly hack to watch iplayer/hulu that requires a tremendous amount of upkeep with large chances of failure.  Hulu doesn't work and will likely never work again in mythvodka.  Even if it did work, it is probably illegal to actually download the content to your computer and encode it (which is how vodka works).  What prevents you from keeping it for example.

I have moved on to Boxee.  They just released a new version yesterday for ubuntu, and it is 100 times more stable than the previous version.  It has a hulu plugin (which works) and a iplayer plugin (which I assume works, but I don't live in UK).  It also just plays the flash stream, so it does not have legality issues (although playback may not be quite as smooth).  Also, the more linux users we have using boxee, the better the linux version will become. 

I launch Boxee from my mythtv frontend.  It automatically recognizes my mce remote, and when I close boxee I am back at the mythtv frontend.  To do this just add a menu item to mythtv as follows

Edit your mainmenu.xml with the following entry:

<button>
<type>MENU_MEDIA_LIBRARY</type>
<text>Boxee</text>
<action>EXEC /opt/boxee/run-boxee-desktop</action>
</button>

Not to be a downer, but I really recommend abandoning mythvodka.  I wasted many hours of my life getting it working (and it never really worked well), and then hulu killed it.  I don't think it is worth your time.

Anyway, that is my two-cents about this whole thread.

---

### Post by mikeglover on 2009-04-28
> **jdeslip said:**
> Lets face it, mythvodka is at the best of times a buggy/ugly hack to watch iplayer/hulu that requires a tremendous amount of upkeep with large chances of failure.  Hulu doesn't work and will likely never work again in mythvodka.  Even if it did work, it is probably illegal to actually download the content to your computer and encode it (which is how vodka works).  What prevents you from keeping it for example.

I have moved on to Boxee.  They just released a new version yesterday for ubuntu, and it is 100 times more stable than the previous version.  It has a hulu plugin (which works) and a iplayer plugin (which I assume works, but I don't live in UK).  It also just plays the flash stream, so it does not have legality issues (although playback may not be quite as smooth).  Also, the more linux users we have using boxee, the better the linux version will become. 

I launch Boxee from my mythtv frontend.  It automatically recognizes my mce remote, and when I close boxee I am back at the mythtv frontend.  To do this just add a menu item to mythtv as follows

Edit your mainmenu.xml with the following entry:

<button>
<type>MENU_MEDIA_LIBRARY</type>
<text>Boxee</text>
<action>EXEC /opt/boxee/run-boxee-desktop</action>
</button>

Not to be a downer, but I really recommend abandoning mythvodka.  I wasted many hours of my life getting it working (and it never really worked well), and then hulu killed it.  I don't think it is worth your time.

Anyway, that is my two-cents about this whole thread.

Had a quick look at the website for Boxee. Havn't heard of it before. Looks much better. I think I'm gonna give up on Mythvodka, I spent a long time on this as well and wasted time that I could of spent watching my BBC iPlayer programmes.

I'll try out Boxee tonight and see if I have better luck.
Thanks for the advise.

---

### Post by mikeglover on 2009-04-29
Installed Boxee last night. Works perfectly. 100 times better than MythVodka.
Recommend anyone trying to use MythVodka to check out Boxee. Installed the deb file from website and it works. Now I can get on and catchup with Ashes to Ashes. :)

---

### Post by kadafi69 on 2009-04-29
Ive installed Boxee too, but cant seem to get my remote to work :(

---

### Post by jdeslip on 2009-04-29
You might have to edit the file ~/.boxee/UserData/Lircmap.xml - there are a few remotes in their by default (mceusb remote being one).  If yours is not, try editing the file to include it.

---

### Post by awaterson on 2009-05-04
Hi,  Sorry if this has already been asked / addressed.  I am currently running .22 (trunk) on mythbuntu and have been trying to compile mythvodka for a couple of weeks now without success.  I am running amd64 environment, but have followed the guides and continue to get errors.  Has any one managed to successfully compile this for trunk and amd64 yet if so any instructions on what to change would be helpful.

Thanks

Andy

---

### Post by pau1mi11er on 2009-05-11
Right,

I'll give Boxee a go - installed it and superficially it looks great - much better user interface. But...

Boxee only plays iPlayer for 20 seconds and then stops. No known fix yet apparently

And now MythVodka has stopped working! It throws me out to the desktop whenever I try to do something.

So - no iPlayer for me at the moment until I can gather the time to do something.

Such is life.

Paul

---

### Post by pau1mi11er on 2009-05-18
Right, here we go.

Still can't get Boxee to show more than 20 seconds of iPlayer so got to work on MythVodka again.

Found out why it does not work - it's a coincidental failure of the [www.bewhere.co.uk](www.bewhere.co.uk) xml feed for revision3.

Took this out of the MythVodka settings (it does not matter because revision3 etc works fine in Boxee) and hey-presto! IPlayer starts working again.

So, got all the good bits going and now just need to get the ssh proxy to my web server in the US up on demand and I've got the world to look at (well almost)

Paul

---

### Post by Indubitableness on 2009-06-21
> **nrune said:**
> ```
you need to download all the mythtv 0.21 sourcecode 
```

```
and build the plugin from within the tree once you have configured mythtv and mythtvplugins.
```

Thanks

From within which tree? From the source code for the mythplugins? That would be ~/build/mythpluginsblahdeblah for me. Or like, from within /usr/share/mythtv?

I'm confused on where I need to extract the mythvodka source before I compile it.

---

### Post by Dubstar_04 on 2009-06-22
I have done more work on the mythvodka plugin, it now will only work for the uk iplayer streams but it works much better. see screenshot:

[http://picasaweb.google.co.uk/lh/photo/KmivZFSUgXtMDUPpBwHqsg?authkey=Gv1sRgCI_Ei5rFm4HL3AE&feat=directlink](http://picasaweb.google.co.uk/lh/photo/KmivZFSUgXtMDUPpBwHqsg?authkey=Gv1sRgCI_Ei5rFm4HL3AE&feat=directlink)

if anyone wants a go let me know and I will upload it somewhere.

Indubitableness,

There are a few things you need to do to be able to build plugins.

1. you need the correct mythtv source [mythtv website]("http://svn.mythtv.org/trac/wiki")

2. you need the dependencies for building mythtv. this used to be as simple as doing
```
sudo apt-get build-dep mythtv
``` 

but this no longer works. but try it first, then if it fails try something like this: 

```
sudo apt-get install autotools-dev ccache comerr-dev debhelper dpatch gettext html2text intltool-debian libartsc0-dev libasound2-dev libaudio-dev libavc1394-dev libcups2-dev libcupsys2-dev libdts-dev libdvb-dev libdvdnav-dev libdvdnav4 libdvdread-dev libexpat1-dev libfaac-dev libfaad-dev libfftw3-dev libfontconfig1-dev libfreetype6-dev libgcrypt11-dev libgif-dev libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev libgnutls-dev libgpg-error-dev libice-dev libiec61883-dev libimlib2-dev libjack-dev libjack0.100.0-dev libjpeg62-dev libkadm55 libkrb5-dev liblcms1-dev liblircclient-dev libltdl7-dev libmail-sendmail-perl libmng-dev libmysqlclient15-dev libogg-dev libpng12-dev libpthread-stubs0 libpthread-stubs0-dev libqt3-compat-headers libqt3-headers libqt3-mt-dev libraw1394-dev libsm-dev libsys-hostname-long-perl libtasn1-3-dev libtiff4-dev libtiffxx0c2 libtool libungif4-dev libvorbis-dev libx11-dev libx264-dev libxau-dev libxcb-xlib0-dev libxcb1-dev libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxmu-dev libxmu-headers libxrandr-dev libxrender-dev libxt-dev libxv-dev libxvidcore4-dev libxvmc-dev libxxf86vm-dev mesa-common-dev patchutils po-debconf qt3-dev-tools texi2html x11proto-core-dev x11proto-fixes-dev 11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
```

once this is done you need the plugin source for the correct build of mythtv (0.21 or 0.22 (trunk))

3. place the plugin source in the plugin directory /home/user/release-0-21-fixes/mythplugins

4. build mythtv, no need to install.

terminal:

```


cd release-0-21-fixes/mythtv

./configure 

sudo make


```

5. build and install your plugin. 

```

cd ../

cd mythplugins

./configure

cd myth'plugin of choice'

qmake

sudo make

sudo make install


```


Make sure there are entries in the mythtv menus for the plugin you are installing or it wont show up!!

it might complain when you try to build the plugins, just read the error message and copy the correct files from the source folder to wherever they are needed.

---

### Post by steve.vinbiz on 2009-06-30
I have successfully compiled this on amd64 with mythtv trunk 0.22 and r12 svn of mythvodka. Everything appears ok but I get no feeds or streams once configured. The settings are added to mysql but I do not have the streams_feeds or streams_streams tables in my database. I am in the UK and get_iplayer works fine from the command line. Any ideas ?

---

### Post by steve.vinbiz on 2009-07-01
Actually - scrap the above. Just found [http://linuxcentre.net/projects/get_iplayer-pvr-manager/](http://linuxcentre.net/projects/get_iplayer-pvr-manager/). Brilliant, wont be going near mythvodka for a while

---

### Post by mludowise on 2009-07-15
> **jdeslip said:**
> Lets face it, mythvodka is at the best of times a buggy/ugly hack to watch iplayer/hulu that requires a tremendous amount of upkeep with large chances of failure.  Hulu doesn't work and will likely never work again in mythvodka.  Even if it did work, it is probably illegal to actually download the content to your computer and encode it (which is how vodka works).  What prevents you from keeping it for example.

I have moved on to Boxee.  They just released a new version yesterday for ubuntu, and it is 100 times more stable than the previous version.  It has a hulu plugin (which works) and a iplayer plugin (which I assume works, but I don't live in UK).  It also just plays the flash stream, so it does not have legality issues (although playback may not be quite as smooth).  Also, the more linux users we have using boxee, the better the linux version will become. 

I launch Boxee from my mythtv frontend.  It automatically recognizes my mce remote, and when I close boxee I am back at the mythtv frontend.  To do this just add a menu item to mythtv as follows

Edit your mainmenu.xml with the following entry:

<button>
<type>MENU_MEDIA_LIBRARY</type>
<text>Boxee</text>
<action>EXEC /opt/boxee/run-boxee-desktop</action>
</button>

Not to be a downer, but I really recommend abandoning mythvodka.  I wasted many hours of my life getting it working (and it never really worked well), and then hulu killed it.  I don't think it is worth your time.

Anyway, that is my two-cents about this whole thread.

I just downloaded Boxee today. It doesn't look like Hulu is supported.

---

### Post by highlandsun on 2009-08-09
I haven't looked at the myth code, but I've been talking with the xbmc developers about hulu support. (I have a working script in perl, should be easy for them to rework into python...)

---

### Post by Coume on 2009-08-19
> **Dubstar_04 said:**
> I have done more work on the mythvodka plugin, it now will only work for the uk iplayer streams but it works much better. see screenshot:

[http://picasaweb.google.co.uk/lh/photo/KmivZFSUgXtMDUPpBwHqsg?authkey=Gv1sRgCI_Ei5rFm4HL3AE&feat=directlink](http://picasaweb.google.co.uk/lh/photo/KmivZFSUgXtMDUPpBwHqsg?authkey=Gv1sRgCI_Ei5rFm4HL3AE&feat=directlink)

if anyone wants a go let me know and I will upload it somewhere.

I would love to test the new version out. 
Would you mind posting a link?

I currently use get_iplayer from command as the previous mythvodka version was not working well enough :/

Thanks
Ludo

---

### Post by geekyhawkes on 2009-08-19
I would be very interested to have iplayer integrated within myth, and any work to update mythvodka would be great!

---

### Post by Dubstar_04 on 2009-09-08
Sorry ive not replied in such a long time guys.

I did a fresh install and lost the mythvodka version that I took a screenshot of but I have made one pretty similar. It should work. 

The files are attached, make sure you read the read me and ask if you need help or have any recommendations. 

I won't be doing much more on this because it works for now and mythtv 0.22 is coming out soon.

EDIT: if your having problems try running  sudo /usr/local/bin/mythiplayer/get_iplayer --flush

manually from terminal!!

[**Download here!!**]("http://sites.google.com/site/mythiplayer/")

---

### Post by geekyhawkes on 2009-09-08
Thanks for the upload.  Has anyone had any sucess with this yet?

---

### Post by davetibbs on 2009-09-08
I've tried this but my frontend is crashing at 40% with the error

```
2009-09-09 00:06:48.136 iPlayer Data Has Expired. Refreshing.
2009-09-09 00:06:49.291 Mythiplayer Data Grabber: Executing '/usr/local/bin/mythiplayer/get_iplayer -q --mythtv - --xml-channels'
2009-09-09 00:06:50.154 Grabber Finished. Processing Data.
2009-09-09 00:06:50.155 Error parsing data from grabber: Error: unexpected end of file Location Line: 1 Column 1

```

I've seen previous posts in this thread refer to hulu.xml - is this relevant?  I'm guessing not as it's not running the hulu grabber, rather it's running get_iplayer.  Could this be a permissions issue?  Anything else I can try?

Cheers

---

### Post by Keithamus on 2009-09-08
I get something very similar:

```

2009-09-09 01:14:07.545 Unable to find image file: /usr/share/mythtv/themes/blootube-wide/iplayer-logo.png
2009-09-09 01:14:07.546 UIImageType::LoadImage() - Cannot find image: iplayer-logo.png
2009-09-09 01:14:07.779 New DB connection, total: 4
2009-09-09 01:14:17.812 Connected to database 'mythconverg' at host: 192.168.0.103
2009-09-09 01:14:17.813 iPlayer Data Has Expired. Refreshing.
2009-09-09 01:14:18.827 Mythiplayer Data Grabber: Executing '/usr/local/bin/mythiplayer/get_iplayer -q --mythtv - --xml-channels'
2009-09-09 01:14:19.515 Grabber Finished. Processing Data.
2009-09-09 01:14:19.515 Error parsing data from grabber: Error: unexpected end of file Location Line: 1 Column 1

```

Running the get_iplayer command manually seems to do nothing...

Here is my /var/tmp/mythiplayer directory. All of the files contain content:

```

cactuar@cactuar:/var/tmp/mythiplayer$ ls -lah
total 152K
drwxr-xr-x 2 cactuar cactuar 4.0K 2009-09-09 01:04 .
drwxrwxrwt 3 root    root    4.0K 2009-09-09 01:04 ..
-rw-r--r-- 1 root    root    9.4K 2009-09-09 01:04 BBC Alba
-rw-r--r-- 1 root    root    9.5K 2009-09-09 01:04 BBC Four
-rw-r--r-- 1 root    root    6.9K 2009-09-09 01:04 BBC HD
-rw-r--r-- 1 root    root     11K 2009-09-09 01:04 BBC News
-rw-r--r-- 1 root    root     11K 2009-09-09 01:04 BBC News 24
-rw-r--r-- 1 root    root     11K 2009-09-09 01:04 BBC One
-rw-r--r-- 1 root    root    6.6K 2009-09-09 01:04 BBC Parliament
-rw-r--r-- 1 root    root    7.6K 2009-09-09 01:04 BBC Sport
-rw-r--r-- 1 root    root    4.3K 2009-09-09 01:04 BBC Three
-rw-r--r-- 1 root    root     11K 2009-09-09 01:04 BBC Two
-rw-r--r-- 1 root    root     12K 2009-09-09 01:04 CBBC
-rw-r--r-- 1 root    root     13K 2009-09-09 01:04 CBeebies
-rw-r--r-- 1 root    root    9.1K 2009-09-09 01:04 Signed

```

---

### Post by Keithamus on 2009-09-08
The issue is that the script is self updating, when it runs, it tries to update, then crashes out because of write permissions to itself.

A quick fix is to run

```

sudo /usr/local/bin/mythiplayer/get_iplayer

```

Then it'll work fine from then on.

Is working fine for me now, although the buffering does take quite a while.

Great work though. Us brits can finally get on demand telly from our mythboxes. The mrs will be pleased!

---

### Post by Dubstar_04 on 2009-09-09
If your having problems try running the following in terminal:

```
 sudo /usr/local/bin/mythiplayer/get_iplayer --flush
```

and then:

```
/usr/local/bin/mythiplayer/get_iplayer -q --mythtv ~/Desktop/iplayer.xml --xml-channels

```

This should write a iplayer.xml file to your Desktop. check it to make sure its got some information in. 

If people are finding it takes too long to buffer please post how long and I will adjust the plugin to buffer less and therefore play sooner.

I have a lightning fast cable connection so its just right for me.

What you should have is this:

[Screenshot 1]("http://picasaweb.google.co.uk/lh/photo/5xbh_eg4x5Uiau4ybKRYqg?authkey=Gv1sRgCI_Ei5rFm4HL3AE&feat=directlink")

or this:

[Screenshot 2]("http://picasaweb.google.co.uk/lh/photo/3n7nhYcJcWvpLAeYUe-YqQ?authkey=Gv1sRgCI_Ei5rFm4HL3AE&feat=directlink") 

The second one uses a different ui file which is attached. It will need moving to /usr/share/mythtv/themes/default-wide```

```


[**Download here!!**]("http://sites.google.com/site/mythiplayer/")

---

### Post by Dubstar_04 on 2009-09-09
If anyone is having problems with slow buffering, I have attached a new mythiplayer build that should address the problem. 

The package is already built so you should be able to:

cd ~/mythplugins/mythiplayer/mythiplayer

sudo mv libmythiplayer.so /usr/lib/mythtv/plugins/

or 

cd ~/mythplugins/mythiplayer/mythiplayer

make distclean

qmake mythiplayer.pro

make

sudo mv libmythiplayer.so /usr/lib/mythtv/plugins/

Then restart mythfrontend.

If this is too quick and dropping out half way through a programme we can meet in the middle somewhere. 

NOTE: I always set the mythtv default player to 'Internal' for best results. 

Setup -> Media Settings -> Video Settings -> Player Settings 
-> Default Video Player 'Internal'

Be careful as its a capital I in Internal...

Please can you give me some feedback on this?


[**Download here!!**]("http://sites.google.com/site/mythiplayer/")

---

### Post by davetibbs on 2009-09-09
I will try out the new version and report back.

In the meantime, I've now got the script to run (by running get_iplayer --flush as detailed above) but I have "By Feed" > "BBC" > then a list of channels - e.g. BBC1, BBC Alba, etc, but no iPlayer programs.

Is there any reason for this?

---

### Post by Keithamus on 2009-09-09
Tried out your new code, including the new UI and the new small buffer plugin. This is the issue I get:

```

Could not locale 'iplayerui' in theme 'mythiplayer-'.

Returning to the previous menu.

```

---

### Post by Dubstar_04 on 2009-09-09
> **Keithamus said:**
> Tried out your new code, including the new UI and the new small buffer plugin. This is the issue I get:

```

Could not locale 'iplayerui' in theme 'mythiplayer-'.

Returning to the previous menu.

```

This should now be fixed. sorry.

---

### Post by Dubstar_04 on 2009-09-09
> **davetibbs said:**
> I will try out the new version and report back.

In the meantime, I've now got the script to run (by running get_iplayer --flush as detailed above) but I have "By Feed" > "BBC" > then a list of channels - e.g. BBC1, BBC Alba, etc, but no iPlayer programs.

Is there any reason for this?


Its due to the structure of the ui tree. its really annoying but not something I want to spend time changing when myth 0.22 will be out at the end of the month. I will however be working on a new version of the plugin. 

If you keep pressing to the right you will get to the programs.

---

### Post by Keithamus on 2009-09-09
Dubstar, checked out the plugin, working really nicely! Dead chuffed!

One thing I'd like is options to tweak the quality if possible? I've got a fairly fast connection, and it'd be great if I could watch these in a bit higher quality, for example higher res (the current res is 480x272).

How do you know 0.22 will be released this month btw? I've seen nothing about it.

---

### Post by Dubstar_04 on 2009-09-09
> **Keithamus said:**
> Dubstar, checked out the plugin, working really nicely! Dead chuffed!

One thing I'd like is options to tweak the quality if possible? I've got a fairly fast connection, and it'd be great if I could watch these in a bit higher quality, for example higher res (the current res is 480x272).


Im glad its working. there is no way to select the quality at the moment but im sure its possible as the xbmc plugin can do it. Maybe something to add to the 'to do list'!

> **Keithamus said:**
> 
How do you know 0.22 will be released this month btw? I've seen nothing about it.

There should be a feature freeze in the coming days and then a bugsquash before release. I'm not certain, just heard it through the grapevine.

---

### Post by geekyhawkes on 2009-09-09
Its not quite working for me (althought it is probably down to the way i have tried to set it up and not the script!)  I followed the read me, have ran get_player --flush (which seemed to work), plus out putted an .xml file to my desktop that has plenty of data in it.  

The problem i have is that i run the iplayer plugin from within the frontend all i get is a list of

FEEDS->FEEDS->By feed

I have a black square at the bottom right hand corner (which should be the preview), but no data or lists under any of the feeds/feeds/by feed.

Where am i goig wrong?

---

### Post by Dubstar_04 on 2009-09-10
> **geekyhawkes said:**
> Its not quite working for me (althought it is probably down to the way i have tried to set it up and not the script!)  I followed the read me, have ran get_player --flush (which seemed to work), plus out putted an .xml file to my desktop that has plenty of data in it.  

The problem i have is that i run the iplayer plugin from within the frontend all i get is a list of

FEEDS->FEEDS->By feed

I have a black square at the bottom right hand corner (which should be the preview), but no data or lists under any of the feeds/feeds/by feed.

Where am i goig wrong?

Have you tried pressing menu and running the update iplayer from there?

If your running the get_iplayer script manually and its producing a file on your Desktop theres no reason for it not to work. 

Try to update the listings from within the plugin see where we are. 

let me know how you get on.

---

### Post by geekyhawkes on 2009-09-10
I have tried updating the iplayer from within the front end.  I get the % status dialogue box that shows something should be happening, but each time i get dropped back to the feed->feed>By feed UI.

As far as settings go what i have seems sensible;

get_iplayer location:  /usr/local/bin/mythiplayer/get_iplayer
mencoder:              /usr/bin/mencoder
temp folder:           /var/tmp
curl location:         /usr/bin/curl

Is there anything else im missing?


EDIT:  I had to do a full reboot of my machine (as i had update v4l) and the update inside the front end now gives me the channel list as expected. Sadly I am not able to play any files.  Everytime i select the feed to play i just get "opps not available".

How do i know which build of your mythiplayer i have installed (I.E with the increased buffering?)

Thanks for this plugin, if i can get it working it will really increase the WAF of my myth install!

---

### Post by Dubstar_04 on 2009-09-10
Well i'm glad it works for you. I run two mythboxes one in the living room and on in the bedroom and the mrs swears by them. they're our only source of av equipment. 

This plugin is pretty cool however I am sure i can produce something more polished under the mythui of 0.22. 

my to do list looks something like so:

1. Write an iplayer plugin under mythtv 0.22 with a better ui which is more robust
2. Add the ability to download in the background and play later
3. ITV catchup integration
4. Ability to search
5. Option for video quality


Check out this Screenshot:

[Mythtv WebTV]("http://picasaweb.google.co.uk/lh/photo/M194C1D8Ji0R9D2Kns80rg?authkey=Gv1sRgCI_Ei5rFm4HL3AE&feat=directlink")

I think mythtv is about to change in to a Swan!!

---

### Post by Dubstar_04 on 2009-09-10
> **geekyhawkes said:**
> 



EDIT:  I had to do a full reboot of my machine (as i had update v4l) and the update inside the front end now gives me the channel list as expected. Sadly I am not able to play any files.  Everytime i select the feed to play i just get "opps not available".

How do i know which build of your mythiplayer i have installed (I.E with the increased buffering?)

Thanks for this plugin, if i can get it working it will really increase the WAF of my myth install!


Have you got mencoder and curl installed?

Sometimes a user doesnt have the ability to write to /var/tmp.
Try this:

```
 sudo chmod 777 /var/tmp 
```


Try a few different programs too, there are times when some don't play. 

you are almost there. I can't think of anything else.

---

### Post by geekyhawkes on 2009-09-10
Thanks Il give it a whirl.  Without wanting to take the pi$$ is there any chance you could get 4 On Demand to work as well?  

This really is looking like a fantastic plugin for .22!

Thanks again.

EDIT:

Definatly got CURL and mencoder installed and I have chmod'd the tmp directory.  I have also checked that i have Internal specified as the playback program and still get the OOOps!! The selected files doesnt seem to be available dialogue.

Anything else that i might be doing wrong?

---

### Post by Dubstar_04 on 2009-09-10
> **geekyhawkes said:**
>  Without wanting to take the pi$$ is there any chance you could get 4 On Demand to work as well? 

I think 4OD and 5 on demand are DRM'ed so they might well be a no no for us linux folks. Once iPlayer is working properly I may well look into it.

Don't worry about asking for features. I would rather understand the scope of the work before I start writing the code, it saves too much rework.

---

### Post by geekyhawkes on 2009-09-10
Great thanks.  I have tried a few streams from a few different channels and each time i get the same error message.  I can almost see some other screen trying to take the focus and appear ontop but it only flashes for a tiny amount of time and not enough to see what it is.  

Is there anyway i could increase my buffering to see if that is the cause as it seems that can only be the last outstanding issue (unless there is something else you can think off?)

---

### Post by Dubstar_04 on 2009-09-10
Can you confirm you have set the 'Internal' Player as default?

> **Dubstar_04 said:**
> 
NOTE: I always set the mythtv default player to 'Internal' for best results. 

Setup -> Media Settings -> Video Settings -> Player Settings 
-> Default Video Player 'Internal'

Be careful as its a capital I in Internal...



You could try the first package I posted which had quite a long buffer. 

can you run 'mythfrontend' from terminal go to the plugin try and run a programme and post the output when it fails? 

The other thing to try is run mythtv windowed and have /var/tmp open next to it and watch for the download starting and being transcoded to stream.mpg.

you could also try:

```
sudo chmod +X /usr/local/bin/mythiplayer/playiplayer.sh
```

Post the output from running 'mythfrontend' in terminal first and lets have a look.

---

### Post by red321 on 2009-09-12
Just changed up to trunk. When you get somthing going, more than happy to test it out :-)

---

### Post by geekyhawkes on 2009-09-15
Sorry for the delay, just got around to trying to get this working again.

I am back where i strated sort of with FEEDS->FEEDS->By feed displayed after opening mythiplayer and allowing the auto update to work. This is the output from terminal;

2009-09-15 16:36:46.813 Grabber Finished. Processing Data.
2009-09-15 16:36:48.825 Rows: 0

For some reason the grabber doesnt seem to have pulled anything down even though it took a bit of time to reach 100% and display the UI.


I then tried a manual update in the menu in the mythiplayer ui and the following is the terminal result;

2009-09-15 16:39:23.243 Doing Manual Stream Times Update
2009-09-15 16:39:24.357 Mythiplayer Data Grabber: Executing '/usr/local/bin/mythiplayer/get_iplayer -q --mythtv - --xml-channels'
2009-09-15 16:39:34.517 Grabber Finished. Processing Data.
2009-09-15 16:39:36.524 Rows: 0

I then ran a get_iplayer flush and re-updated the iplayer from within myth.  This time when i updated i got a decent amount of traffic in the terminal window with a date/time INSERTING Prog: programme name.

So from what i can see for some reason i have to flush each time before i update the listings for the iplayer.  Is there a way around this, or is that expected?

When i actually try and play the file i then get the oops The selected file doesnt seem to be available dialogue.

Terminal output is;

2009-09-15 17:04:35.196 UIImageType::LoadImage() - Cannot find image: /var/tmp/mythiplayer/Crash
2009-09-15 17:04:35.835 UIImageType::LoadImage() - Cannot find image: /var/tmp/mythiplayer/Doctors: Series 11
2009-09-15 17:04:39.026 Running Command: /usr/local/bin/mythiplayer/get_iplayer  -f --force-download -o /var/tmp/ --file-prefix iplayerdump --get --pid b00mlyh4
2009-09-15 17:04:39.026 Buffer Required: 8000000
2009-09-15 17:04:39.026 Downloading to: /var/tmp/iplayerdump.partial.mov
2009-09-15 17:04:39.068 Running Command: /usr/local/bin/mythiplayer/playiplayer.sh /usr/bin/curl /usr/bin/mencoder b00mlyh4
2009-09-15 17:04:39.068 Buffer Required: 8000000
2009-09-15 17:04:39.799 Selection: File: b00mlyh4


This is consistant across several files.

If i navigate to /var/tmp/mythiplayer then i also dont have any preview images of the shows (reflected by the errors above) but do have the channel logos.


A further manual update (that i halted to capture the heading information) returned the following in terminal;

2009-09-15 17:12:13.616 Doing Manual Stream Times Update
2009-09-15 17:12:14.749 Mythiplayer Data Grabber: Executing '/usr/local/bin/mythiplayer/get_iplayer -q --mythtv - --xml-channels'
2009-09-15 17:12:16.557 Grabber Finished. Processing Data.
2009-09-15 17:12:16.657 Inserting prog: Aifric: Series 1
2009-09-15 17:12:36.660 HttpComms::Timeout for url: [http://www.bbc.co.uk/iplayer/images/episode/b00ld7x5_150_84.jpg](http://www.bbc.co.uk/iplayer/images/episode/b00ld7x5_150_84.jpg)
2009-09-15 17:12:36.670 Server returned an error status code 0 for url: [http://www.bbc.co.uk/iplayer/images/episode/b00ld7x5_150_84.jpg](http://www.bbc.co.uk/iplayer/images/episode/b00ld7x5_150_84.jpg)
2009-09-15 17:12:36.670 HttpComms::done() - NetworkOperation Error on Finish: Request aborted (1): url: 'http://www.bbc.co.uk/iplayer/images/episode/b00ld7x5_150_84.jpg'


Hopefully something in here will give you a clue as to why i have had no luck yet.

Thanks.

---

### Post by Dubstar_04 on 2009-09-15
Are you pressing across on to an actual programme rather than a channel?

You shouldn't have to flush the get_iplayer script as it does it itself. 

It looks like you dont have the correct permissions in the /var/tmp folder. 

Try this again:

```
sudo chmod 777 /var/tmp

```

```
sudo apt-get install libxml-dom-perl 

```


Thanks,

Dubstar_04

---

### Post by geekyhawkes on 2009-09-15
I have tried the 2 commands above but the iplayer is behaving no differently.  I already had libxml-dom-perl at the latest version and the chmod ran (again) without incident.  

I am pressing on to an actual programme (as in as far right as i can go in UI).

Is there anything else i can do?  When i get a chance i will try and create a file or 2 as a normal user in the var/tmp directory to see if that does actually work.

Is there anything else i can try?

---

### Post by Dubstar_04 on 2009-09-15
You need to understand why get_iplayer is not writing to your /var/tmp folder

Try running the command in terminal:

```
/usr/local/bin/mythiplayer/get_iplayer -f --force-download -o /var/tmp/ --file-prefix iplayerdump --get --pid b00mlyh4
```

it should start, if it does look in /var/tmp to check.

if it doesnt post the output.

---

### Post by geekyhawkes on 2009-09-15
This is the output i just have;

get_iplayer v2.30, Copyright (C) 2009 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

INFO Trying to stream pid using type tv
INFO: pid found in cache
Matches:
193:	Doctors: Series 11 - Hello, Hello, Hello, BBC HD, Drama,Medical,Soaps,TV, default,

INFO: 1 Matching Programmes
WARNING: No programmes are available for this pid
INFO: No versions exist for this programme



Thanks for the help, hopefully we will get there soon!

---

### Post by moorsey on 2009-09-16
hey all,

just read this post all the way through.  Is this project being maintained anywhere specific, seems to be a bit everywhere.  Just wondering where the latest version of the plugin is etc.  I saw one posted a few pages back.

Looks great anyway!  Just getting into MythTV, trying to persuade the parents they need one!:P

---

### Post by Dubstar_04 on 2009-09-16
There is a mythvodka googlecode project for the original mythvodka plugin.

The bits and bobs i've been posting are just a few mods I have made to make it work how and want. 

I can put together a quick webpage or something if people think it will help. But like I said mythtv 0.22 will be out before long so this code will die pretty quickly.

Edit: I have thrown together a quick google site page for the work i have done. Its not brilliant but its there at least.

[MythiPlayer]("http://sites.google.com/site/mythiplayer/")

---

### Post by SammyC on 2009-09-16
There's a bug in the code in main.cpp where it creates the streamsui object, it requests iplayerui instead.

Other than that its looking pretty good all things considered! :)

---

### Post by Dubstar_04 on 2009-09-17
> **SammyC said:**
> There's a bug in the code in main.cpp where it creates the streamsui object, it requests iplayerui instead.

Other than that its looking pretty good all things considered! :)

Thats not a bug. I included the incorrect ui file in the original post. 

It works as expected creating the streamsui object looking for the iplyerui layout in the mythiplayer-ui.xml file. 

This is not a bug.

```
 StreamsUI streamsui(gContext->GetMainWindow(), "iplayerui", "mythiplayer-");
```

---

### Post by SammyC on 2009-09-17
Sorry but following your instructions on the google code page means it doesn't work because the included ui file and main.cpp file don't match.

Its not a biggie as it was very simple to fix but I just thought you'd like to know.

I have a different problem now, not sure what is the cause, but it seems like the video quickly gets in front of the audio to the point that a few minutes in and the audio is about 2 seconds behind. Admittedly I only tried with about two files so it may have been teething problems.

have you seen this before and any suggestions to hunt down the problem?

---

### Post by geekyhawkes on 2009-09-17
Any idea what might be causing my issues from my last post?  Is there anything else i can try to track down where things might be going wrong?

---

### Post by Dubstar_04 on 2009-09-17
> **SammyC said:**
> Sorry but following your instructions on the google code page means it doesn't work because the included ui file and main.cpp file don't match.

Its not a biggie as it was very simple to fix but I just thought you'd like to know.

I have a different problem now, not sure what is the cause, but it seems like the video quickly gets in front of the audio to the point that a few minutes in and the audio is about 2 seconds behind. Admittedly I only tried with about two files so it may have been teething problems.

have you seen this before and any suggestions to hunt down the problem?


using mplayer as the default video player normally causes this. 

Try changing it to the Internal player. if you don't know how it was discussed a few posts back. let me know the results.

---

### Post by Dubstar_04 on 2009-09-17
> **geekyhawkes said:**
> This is the output i just have;

get_iplayer v2.30, Copyright (C) 2009 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

INFO Trying to stream pid using type tv
INFO: pid found in cache
Matches:
193:	Doctors: Series 11 - Hello, Hello, Hello, BBC HD, Drama,Medical,Soaps,TV, default,

INFO: 1 Matching Programmes
WARNING: No programmes are available for this pid
INFO: No versions exist for this programme



Thanks for the help, hopefully we will get there soon!

could you try a few different programmes from bbc one whilst running mythfrontend from terminal and post the out come. 

The command you tried last didn't work on my machine either. 

Try and stick to BBC one or two and try a few different programmes a few times and post your mythfrontend log from /var/log/mythtv.

Im stuggling to understand your problem. most people seem to have it working fine. I might have to add some extra debugging to a build and let you try that as i am curious to find the problem now. 

cheers,

Dubstar_04

---

### Post by SammyC on 2009-09-18
Hi Dubstar_04,

Tried again last night and got the same with whatever I tried. I'll check which player I'm using, I thought it was the internal one but thinking back it may not be. When I change the volume I get a on-screen display of the volume changing which I don't think the internal player does?

Cheers for this again, it really is pretty cool.

Have you had any thoughts about offering a choice of resolutions? Would get a bit more complicated because of the need for flvstreamer.

:)

---

### Post by Dubstar_04 on 2009-09-18
> **SammyC said:**
> 

Have you had any thoughts about offering a choice of resolutions? Would get a bit more complicated because of the need for flvstreamer.

:)

I am working on this at the moment but i'm having problems calling functions from popupwindows. I'm not too keen on doing loads of work on this though, as i have said mythtv 0.22 isnt a million miles away and all the work will need to be redone in order to work with mythui.

---

### Post by sarendipidy on 2009-09-18
> **Dubstar_04 said:**
> Thats not a bug. I included the incorrect ui file in the original post.

It works as expected creating the streamsui object looking for the iplyerui layout in the mythiplayer-ui.xml file.

This is not a bug.

```
 StreamsUI streamsui(gContext->GetMainWindow(), "iplayerui", "mythiplayer-");
```

> **SammyC said:**
> Sorry but following your instructions on the google code page means it doesn't work because the included ui file and main.cpp file don't match.

Its not a biggie as it was very simple to fix but I just thought you'd like to know.

I have a different problem now, not sure what is the cause, but it seems like the video quickly gets in front of the audio to the point that a few minutes in and the audio is about 2 seconds behind. Admittedly I only tried with about two files so it may have been teething problems.

have you seen this before and any suggestions to hunt down the problem?

I have this problem at the moment where it says it can't find the iplayerui, what is the method to fix this?

Thanks

---

### Post by Dubstar_04 on 2009-09-19
Download the build from here:

[http://sites.google.com/site/mythiplayer/]("http://sites.google.com/site/mythiplayer/")

---

### Post by SammyC on 2009-09-21
> **Dubstar_04 said:**
> I am working on this at the moment but i'm having problems calling functions from popupwindows. I'm not too keen on doing loads of work on this though, as i have said mythtv 0.22 isnt a million miles away and all the work will need to be redone in order to work with mythui.

How about making it another level of menu, i.e. you can go right again and get a choice of resolutions. If you just click on the programme name you just get the default?

Oh, and changing to internal player fixed that sound problem. Thanks! :)


To fix the problem I had with the UI I changed this in main.cpp:
```
StreamsUI streamsui(gContext->GetMainWindow(), "iplayerui", "mythiplayer-");
```

to this:

```
StreamsUI streamsui(gContext->GetMainWindow(), "streamsui", "mythiplayer-");
```

To get it to work.

---

### Post by eNRGy on 2009-09-24
```
~/mythplugins/mythiplayer/mythiplayer$ qmake mythiplayer.pro 
~/mythplugins/mythiplayer/mythiplayer$ make
make: Nothing to be done for `first'.

```

Hey, what would cause this? I'm trying to follow the instructions but that's as far as I get!

Thanks.

---

### Post by Dubstar_04 on 2009-09-25
try running this first:

```
 make distclean 
```

---

### Post by bergqvistjl on 2009-09-29
hi, ive tried the mythiplayer build that dubstar_04 posted a few posts ago, and it seems to work, i.e. the info regarding the programs and channels downloads fine, but whenever i try to play a program, I get an "Oops!! the selected file doesnt seem to be available" and it doesnt play. My user can write to all the directories mentioned on the setup page. any ideas? are there any specific ports i need to unblock?

EDIT: Just saw geekyhawk's posts and this is what i get when i try to run ```
/usr/local/bin/mythiplayer/get_iplayer -f --force-download -o /var/tmp/ --file-prefix iplayerdump --get --pid b0074s1h
``` manually:

```
get_iplayer v2.40, Copyright (C) 2009 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

INFO Trying to stream pid using type tv
INFO: pid found in cache
Matches:
72:	Bleak House - Episode 3, BBC HD, Classic & Period,Drama,TV, default,

INFO: 1 Matching Programmes
INFO: Checking existence of default version
INFO: No specified modes (iphone) available for this programme with version 'default' (try modes: )
ERROR: Failed to record 'Bleak House - Episode 3 (b0074s1h)'

```

---

### Post by Neon Dusk on 2009-09-29
It looks like you're trying to download a BBC HD program using the iphone mode. For BBC HD programmes you would need to use flashhd mode and have flvstreamer installed. 
The get_iplayer command would be 
```

get_iplayer -f --force-download -o /var/tmp/ --file-prefix iplayerdump --mode flashhd --get --pid b0074s1h
```

If flvstreamer isn't in your path you would need to add
```
--flvstreamer /pathto/flvstreamer
```

I gave up using MythVodka a long time ago. Instead I use xbmc-iplayerv2 plugin and have a link to xbmc from the Myth frontend.

---

### Post by bergqvistjl on 2009-09-30
yeh, i tried that and i got further. however, i think my university must be blocking some ports, as it just hangs on "connecting". i've tried to download other (non-iplayer) rtmp streams and it will stream, but it just doesnt download. do you know if there are any rtmp ports i could try and persuade my uni to unblock?

---

### Post by Keithamus on 2009-10-16
Any progress being made for porting this to Mythtv 0.22? Mythbuntu is in beta and 0.22 is in RC phase, so it'd be good timing to start getting this ready for release.

I'd really like to help test and code the little bits I can do.

---

### Post by notaktak on 2009-11-06
> **Keithamus said:**
> Any progress being made for porting this to Mythtv 0.22? Mythbuntu is in beta and 0.22 is in RC phase, so it'd be good timing to start getting this ready for release.

I'd really like to help test and code the little bits I can do.

I've got mythiplayer running in 0.22 on mythbuntu 9.10, A lot of the changes are just to support qt4, although I have also:
- moved the mencoder call into the code itself, removing the need for scripts/playiplayer.sh
- made the get_iplayer call pass its output straight to mencoder, removing the need for the intermediate file (this may not be possible in qt3, but it's possible in qt4)
- added in various flash grabbing options for cases where the iphone feed is unavailable (these probably won't work if you don't have flvstreamer installed - I don't know)
- moved the icons into /usr/share/mythtv/mythiplayer from /var/tmp

I installed the source code from the mythtv website, although I'm not certain it was necessary to do so, and put the mythiplayer directory into the mythplugins subdirectory of that to build, and also had to create the file mythtv/mythplugins/mythconfig.mak with the following contents:
PREFIX=/usr/
LIBDIR=/usr/lib/

I've also hardcoded the version id in one of the header files because I couldn't be bothered to figure out where/how it was meant to be set properly

The attachment is just the mythiplayer subdirectory, so you'll need to download the source from the website, and then place this over the top

If you have installed the qt3 development environment (quite possible if you've tried the various installation steps listed around the place) you'll need to run qmake-qt4 instead of just qmake

The other things I did differently from the instructions provided on the website were to:
copy the contents of the images directory to /usr/share/mythtv/mythiplayer instead of /var/tmp, and place the <button> xml into the appropriate files for the default theme, which in my case was /usr/share/mythtv/themes/defaultmenu/

oh, and a minor correction to the files posted here: line 581 of streamsui.cpp should read:
		 QString localImageFile = tempfolder + "/mythiplayer/" + m.name ;

---

### Post by Dubstar_04 on 2009-11-26
This needs updating to use mythui. I dont have time to do it at the moment.

---

### Post by LuckySmith on 2012-05-12
Not a hard matter to [access Hulu outside US]("http://www.bestvpn.co.uk/watch-hulu-outside-usa/"), because proxy servers and some HTML techniques can make this possible. Be careful to read instructions on manual of vpn router and act upon as it is said in it.

---

### Post by tgm4883 on 2012-05-12
Locking thread due to necromancy. Please check the date of the thread before posting.

---

