---
title: "ipod shuffle"
date: 2009-04-10
forum: Multimedia Software
---

### Post by accodata on 2009-04-10
Hi

I have a ipod shuffle, what is a good program to use with ubuntu 8.10?

thanks


Accodata

---

### Post by utnubuuser on 2009-04-10
gtkpod?

---

### Post by felichas on 2009-04-20
> **utnubuuser said:**
> gtkpod?

gtkpod does not support 3rd generation shuffle (6th generation for gtkpod team).

Does anybody know about a linux program supporting **Ipod Shuffle 3rd generation (4GB)**????

---

### Post by seaq on 2009-05-17
just at the same page... looking for something for the shuffle 3rd gen...  i'm gonna initiliaze it using iTunes meanwhile... :(

---

### Post by bucketoclams on 2009-05-17
Dunno if it helps, but it mounts just fine for me and Amarok recognizes it at /media/ipod. Though it won't find any of the music I have on there...That may be my fault, though. Amarok's being sassy about anything that's .m4a or .mp3 right now. Running Jaunty netbook remix on an eee box.

edit: "it" being the 4gb silver shuffle 3rd generation.

---

### Post by seaq on 2009-05-17
not your fault at all.

As is a very recent model libgpod doesn't have support for it yet.

I just made the homework, send to libgpod devels the data for the BLACK model and someone previously emailed the SILVER model data.  They're just at the CVS at this time, but the internals modifications to the iTunesDB hadn't been researched yet by the devs.

So at this point in time it won't work at all.

Meanwhile I'm using it throught VBOX and iTunes.

I hope the devs can take a look on it to make it work.

---

### Post by geofio on 2009-07-07
Hi, 

please post any updates on the issue here! 

Thanks a lot! 

Ciao, ciao, 

geofio

---

### Post by chistell on 2009-07-19
> **seaq said:**
> not your fault at all.

As is a very recent model libgpod doesn't have support for it yet.

I just made the homework, send to libgpod devels the data for the BLACK model and someone previously emailed the SILVER model data.  They're just at the CVS at this time, but the internals modifications to the iTunesDB hadn't been researched yet by the devs.

So at this point in time it won't work at all.

Meanwhile I'm using it throught VBOX and iTunes.

I hope the devs can take a look on it to make it work.

Hi excuse me, I'm a true ignorant what is VBOX? :confused:
hope too someone will make it work otherwise I don't have any axcess to windows anymore!!!!

---

### Post by felichas on 2009-07-19
> **chistell said:**
> Hi excuse me, I'm a true ignorant what is VBOX? :confused:

[Virtual Box]("http://en.wikipedia.org/wiki/Virtual_box")
If no other solution is available, you can always run a windows virtual computer within your linux with the unsupported apps you really need.

In Spanish there is a name for this: "Matar moscas a cañonazos" (kill flies with a cannon).

---

### Post by chistell on 2009-07-19
ciao Felichas, gracias but I guess I'll charge all my music from some friends pc and then wait untill they solve the problem...or sell the damn shuffle!!!! :mad:

---

### Post by msx2 on 2009-08-08
Any new about this development?

I have the same problem, and i hate use windows from samba files to manage my files...

Ipod Shuffle 4GB (voice over) - Silver.

Regards,

---

### Post by Charybdisz on 2009-10-12
Hello,

how can I use my Ipod Shuffle 2009 edition? It is the newest Ipod Shuffle 4GB model.

I looked everywhere, seems like not a single program supports the Ipod Shuffle! Please help me!

---

### Post by chistell on 2009-12-22
ciao everybody, I've been far away from pc for some months hoped someone had solved the problem meanwhile but it does not seem...any news at all for the damnd Ipod shuffle 4gb????!!!!

---

### Post by Ausmosis on 2009-12-24
Hi,

I would appreciate any feedback as well. I have a 4GB iPod Shuffle 3rd Generation and it still doesn't seem to be supported?... Any advice on when it will be supported would be appreciated. :)

Rgds

Aus...

---

### Post by deadalus.globalnode on 2009-12-24
Have you tried banshee? Also you could try itunes in wine, I have had good luck with that so far, never transferred music to my ipod with that setup though.

---

### Post by doug-M on 2009-12-25
I just ended up with a 3rd Generation Shuffle (with voice), often referred to as 4th gen by plugin developers.

As far as I can tell it doesn't work with anything except iTunes. No other software on Linux or Windows seems to support it.

For example Winamp on windows has iPod support but does not work with the voice enabled iPod shuffle.

I found some information on the database format here: [http://shuffle3db.wikispaces.com/](http://shuffle3db.wikispaces.com/)

GTKPod says it doesn't support yet:
"Note: Can be identified but not fully supported yet due to a different database format. Full support available soon."
[http://gtkpod.wikispaces.com/Supported+iPods#ShuffleFourth](http://gtkpod.wikispaces.com/Supported+iPods#ShuffleFourth)

Sometimes I really hate Apple. 

It seems that if you use Apple products in exactly the way Apple wants you to, then you will love them. If you try to step away from the one true Apple path, then you will hate Apple products.

---

### Post by clausfod on 2009-12-29
Any update on this topic :-) ?

---

### Post by r-senior on 2009-12-30
Having received a 4GB iPod Shuffle as a Christmas present, I am in the same boat. It would appear that Apple have changed the format of the indexing on this generation of iPod.

It comes up as a USB device in Ubuntu, Rhythmbox recognises it, and I can load MP3 files onto it. But it doesn't rebuild the indexes and it won't play: "Please use iTunes to sync music to this iPod" is all I get when I switch it on.

I've tried gtkPod and, again, it's recognised but there's no option for this model of player. Tried another Shuffle model in the drop-down, but it won't rebuild the indexes. 

Found a Python script called rebuild_db and that runs and does something that looks promising but it won't play anything.

[http://shuffle-db.sourceforge.net/]("http://shuffle-db.sourceforge.net/")

Tried the latest release of gnupod but couldn't get it to build. Got some errors about SHA1 that I didn't look into. I should go back and try that again I guess. There appears to have been some recent development to create v0.99.8.

[http://www.gnu.org/software/gnupod/]("http://www.gnu.org/software/gnupod/")

Looking at the gtkPod mailing lists, it looks like there isn't the development resource to support this Shuffle in the near future:

[gtkPod mailing list post 1]("http://sourceforge.net/mailarchive/forum.php?thread_name=c0876fa10910190549o2a849ae5sce4556f871abe721%40mail.gmail.com&forum_name=gtkpod-devel")

[gtkPod mailing list post 2]("http://sourceforge.net/mailarchive/forum.php?thread_name=d45479530910132312s258dab99n1c59a40132725ae2%40mail.gmail.com&forum_name=gtkpod-devel")

This is surely the fundamental problem? With no libgpod support, other interfaces like gtkPod and Rhythmbox aren't going to provide it. Maybe the Python script will be updated?

So I reluctantly admitted defeat and installed v7 iTunes on my Windows 2000 VM in Virtualbox. No joy. This 4GB Shuffle needs a v8 iTunes or later. I could not install the latest version of iTunes on Windows 2000.

My laptop came with Vista but no installation disk, so, even though I have a Windows licence, I can't make a Vista VM to install iTunes. No way am I going to scrub my Karmic installation and put Vista back using the recovery disks. 

I also tried CopyTrans but that needs a recent installation of iTunes in place to get the drivers.

[http://www.copytrans.net/copytransmanager.php]("http://www.copytrans.net/copytransmanager.php")

So, all in all, it's very small and very light but currently useless in a free software world.

If anyone has any other ideas they would be most welcome.

---

### Post by clausfod on 2009-12-30
Thank you for trying and sharing your "investigation" with us :-)

For now I will use my Windows desktop machine with ITunes to be able to use the IPOD Shuffle. Hope that Ubuntu in the future will support the new generation of IPOD Shuffle....

Happy New Year
Claus 
Denmark

---

### Post by r-senior on 2009-12-31
I've still not found a complete Ubuntu solution but I can report that at least my Shuffle is working. Playing, shuffling, etc. \\:D/ I installed MediaMonkey on my Windows 2000 VM in Virtualbox and used that to rebuild the Shuffle database.

So it's definitely a case of "Matar moscas a cañonazos", as felichas puts it, but I can sync my library to the iPod using Ubuntu, managing it with Sound Juicer, Rhythmbox, MusicBrainz Picard *et al*.

```
$ rsync -v -a ~/Music/ /media/IPOD/Music/
```Creating a virtual drive based on ~/Music/ also works but I don't like the way MediaMonkey organises (or, to be more accurate, doesn't organise) the files on the iPod.

Then it's just a case of using the "cannon" in the shape of MediaMonkey to rebuild the indexes. At least this solves my Windows 2000/iTunes dilemma.

---

### Post by formol on 2009-12-31
for my iPod (Classic, 6th gen) I use Floola. 
maybe it work with the Shuffle. 

[http://www.floola.com/modules/wiwimod/index.php?page=WiwiHome](http://www.floola.com/modules/wiwimod/index.php?page=WiwiHome)

---

### Post by r-senior on 2009-12-31
Good suggestion. =D>

I had to fiddle to get 32-bit libstdc++5 on 64-bit Karmic ...

[http://agentzlerich.blogspot.com/2009/11/getting-32-bit-libstdcso5-in-karmic.html]("http://agentzlerich.blogspot.com/2009/11/getting-32-bit-libstdcso5-in-karmic.html")

I plugged in the Shuffle. It recognised it as a Shuffle. Good sign. But then it said the working database was corrupt. Hmm. Not a good sign. But, nothing ventured, nothing gained so I let it "fix" it anyway ... 

And I got ...

"Please use iTunes to sync to this iPod" ](*,)

So it looks like the new database structure in this 4GB ipod Shuffle is not supported. Shame.

But, thanks, it was a good suggestion.

---

### Post by chistell on 2010-01-05
:confused: thanks too, to the friends that has reported all the hard steps to make it work, but for me it seems too complicated and guess I don't like to "matar moscas a canonanzas" so I'll keep waiting hopefully for gtkpod to solve the issue...otherwise guess I'll prefer to get rid of the shuffle rather than get back to windows!!!!
seems to me apple is complicating things  'cause ubuntu has taken all those people that tired of windows waited for a good occasion to switch to mac, or I should rather say to have the money to switch to mac!!!!
I'll stay with ubuntu :KS

---

### Post by r-senior on 2010-01-05
You are right, Apple are complicating things. Or, to be more specific, they are restricting the openness of their players by shifting the indexing into a piece of Apple software, i.e. iTunes. I suspect the motivation is to promote their iTunes store, iTunes gift cards, etc., rather than knock Linux but that is a side effect. Is it anti-competitive? I'd say so.

The engraving service is another neat trick that reduces the after-market value of iPods. And, with the Shuffle, putting the volume control on the headphones means you can't use other headphone brands.

I am sure that gtkPod *et al* will prevail :)

I have a Sony Walkman and that's a breeze with Linux because the player does the indexing. Just drag the Music folder from Ubuntu onto the player. Or use Rhythmbox, etc. When it's unmounted, the player itself works out the indexing and shuffling. That's an open solution.

---

### Post by doug-M on 2010-01-05
Well my solution has been to return the iPod Shuffle, I wish Apple wasn't so closed.

---

### Post by kseise on 2010-01-18
I am still hoping for a solution to this.  I just got the 4th generation shuffle last week.  I didn't research it well enough before hand (for FOSS compatibility).  I needed either the 3rd generation or 4th generation shuffle for my swimming headphones.  Very cool BTW.  

Now I have to use a virtual XP copy to manage the ipod.  That wouldn't be too bad, but when I setup the file share from /home/kseise/Music to the virtual machine on M:\ my itunes will not import the full library.  It only imports a few artists and then just calls it a day.  Anybody figured out why itunes does an incomplete import of libraries on a virtual machine?

---

### Post by imafatmess on 2010-02-06
> **kseise said:**
> I am still hoping for a solution to this.  I just got the 4th generation shuffle last week.  I didn't research it well enough before hand (for FOSS compatibility).  I needed either the 3rd generation or 4th generation shuffle for my swimming headphones.  Very cool BTW.  

Now I have to use a virtual XP copy to manage the ipod.  That wouldn't be too bad, but when I setup the file share from /home/kseise/Music to the virtual machine on M:\ my itunes will not import the full library.  It only imports a few artists and then just calls it a day.  Anybody figured out why itunes does an incomplete import of libraries on a virtual machine?

I have found it generally does on windows anyway. It's a piece of bull tbh

---

### Post by Floola on 2010-03-16
Floola 5.5 now supports shuffle3G (4th gen shuffle does not exist AFAIK)

Visit [http://www.floola.com](http://www.floola.com)

---

### Post by GSF1200S on 2010-05-11
> **Floola said:**
> Floola 5.5 now supports shuffle3G (4th gen shuffle does not exist AFAIK)

Visit [http://www.floola.com](http://www.floola.com)

I bought a 2GB pink ipod shuffle (P/N: MC387LL/A) for my mom (because she wanted one badly) and using the latest floola, I still get "Please use itunes to sync music to this ipod"

Ive tried the latest development release of libgpod, gtkpod, rebuild_db python script and anything else I could find and nothing works. I would sell the shuffle, but its my mom's, and now she's talking about wiping Ubuntu off her computer so she can use her ipod :( Im in the market for an mp3 player myself, and it surely wont be an apple product- they screwed themselves (not that they care- theyve got plenty of people who dont care about freedom to vampire money and compliance from).

Jesus, cant I use a **** music player I PAID FOR without some a-hole forcing his way into my life?! I hate proprietary crap.

---

### Post by pip182 on 2010-06-19
A fix that worked for me and be found here. [http://ubuntuforums.org/showthread.php?t=1357313&highlight=ipod+shuffle+3rd+gen&page=2](http://ubuntuforums.org/showthread.php?t=1357313&highlight=ipod+shuffle+3rd+gen&page=2)

Hope it helps out

---

### Post by kseise on 2010-09-06
Apparently the developers at libgpod and GTKpod have released an updated version of the two packages that we need to accomplish this.  GTKpod is now up to version 1.0 and libgpod is 0.74.  Now all we need to do is wait for the Ubuntu team to pull them into the repositories.  I tried compiling libgpod, but was running into some errors about software versions.

---

### Post by Charybdisz on 2011-02-20
If I would buy a portable music player today, I would choose the Sansa Clip+ MP3 Player, and not the ipod. Sansa Clip+ is cheaper, can play Ogg Vorbis and FLAC by default, doesn't require any program to manage it, and has great music quality.

So if you listen to me, don't buy an ipod! I was a fool when I bought the ipod shuffle!

---

### Post by ClarNik on 2011-02-21
I'm not **totally[B]**[/B] sure about Ipod shuffle, so feel free to dispute this. Have you thought to try the hippo ipod player or perhaps rythmbox? I know for my Ipod Rythymbox works just fine for me, but for some reason none of the other 'ipod organizers' work for it. 
I have a 4GB 3rd gen Ipod...I think...I just know it's fat and square and silver.

---

### Post by patjennings on 2011-05-23
I recently got this model ipod 3rd gen black shuffle ( with earphones volume control ) to work with gtkpod by using 4th gen black preset. It show up in banshee which is my music player of choice but when you drag music into it, it shows up in banshee and in the ipods music folder, but will not play. Shame, I will just use gtkpod with this device.

---

### Post by BobMarleyy on 2011-08-13
Rhythmbox, with the iPod plug-in installed, appears to be removing and adding songs from/to my iPod Shuffle (with VoiceOver), but I have got problems using VoiceOver.
VoiceOver is installed on an iPod Shuffle to read aloud what it is playing. This is very useful, since the iPod Shuffle has no screen on it.

First I got my iPod working properly with VoiceOver activated (all done in iTunes). However when creating/renaming songs/playlists in Rhythmbox, VoiceOver does not work anymore: it does not tell me what is playing. This is only true for the files I changed in Rhythmbox.
Has anyone found a way to use Ubuntu (and Rhythmbox) to create files on an iPod Shuffle that VoiceOver can read so it tells you what is playing?

I already searched this forum and some others, but I have yet to find the solution. I also tried different programs, e.g. GtkPod, Banshee, Hippo (or something). VirtualBox might be an option, but I haven't got any windows CD or anything.

Thank you in advance,
Bob

---

### Post by formol on 2011-08-14
It's not open source, but did you try Floola ?

---

### Post by BobMarleyy on 2011-08-16
> **formol said:**
> It's not open source, but did you try Floola ?

Floola also cannot use the VoiceOver function on my iPod Shuffle, but thank you for the suggestion. I just tried Floola, but it seems to be having more difficulty handling my iPod than Rhythmbox...

If someone manages to create songs on an iPod Shuffle with VoiceOver function in Ubuntu, please let me know!

---

### Post by kendon on 2011-08-27
[http://shuffle-db.sourceforge.net/](http://shuffle-db.sourceforge.net/)

works fine with my 2nd gen shuffle. just shove the mp3s on the usb storage mounted ipod, run the script and listen.

i would be interested to know if this works with 4th gen as well, would be nice if someone tested this and posted the results.

---

### Post by BobMarleyy on 2011-09-02
I've got the 4th gen shuffle. Unfortunately, shuffle-db does absolutely nothing for me. The only function that I got working is renaming the files, but I could not play any song. I wouldn't recommend using shuffle-db on the 4th gen shuffle.

Is VoiceOver also used on the 2nd gen shuffle?

Has anyone got VoiceOver working on a 4th gen iPod shuffle?

Cheers,
Bob

---

### Post by shantiq on 2011-09-02
Please sell it  :KS:KS:KS:KS:


bloody useless piece of krap that only works on their stupid machines with their stupid software Itunes

nazi computing machines and software     :KS:KS


a "normal"    mp3 player  ( not   Ipod  Ikrap  IF*ck  )    will simply take files you drag in from any platform and guess what you can also share it   with any of your friends wherever and whenever   I HAVE USED A  samsung for the last few years and i do what i want with my files   it is supple and easy to use on windows mac and linux


computing as freedom    NOT  use my machine my software buy from my shop etc...



[B]  new campaign from me 
[/B]
```
I-boycott Macs Ipods

```   i run that in my terminal every morning and enjoin others to do same

HHHHHHHHHHHHaa     i feel better  sorry guys   :KS:KS  i loathe all this stuff    just what Linux always set out to avoid

COMPUTING AS FREEDOM      .....NOT AS CORPORATE STRAIGHTJACKET



Please sell it ..

---

