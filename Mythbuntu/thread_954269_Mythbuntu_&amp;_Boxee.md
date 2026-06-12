---
title: "Mythbuntu &amp; Boxee"
date: 2008-10-21
forum: Mythbuntu
---

### Post by bmathis on 2008-10-21
Anyone get these two bad boys working together? It seems that Boxee has a cool new features like hulu and nbc shows that you can watch in the boxee interface. It would be awesome to get these things working in harmony for my viewing pleasure.

EDIT: And by working together, I mean adding Boxee features to Mythbuntu or using them without having to exit Mythfrontend. If its not possible, no biggie ;)

---

### Post by Meph1st0 on 2008-11-12
I just heard about a service called Boxee and it sounds really interesting.  From what I gather it's a type of IPTV service that will stream episodes online.  I noticed on their main page that it has a client for Linux.  Could this be an additional Mythtv plugin to include boxee service?  It doesn't look like it makes use of any sort of tv capture or tuner cards so I don't think it's a replacement for Mythtv but a I think it could be a really cool plugin.

If anyone knows anything more about Boxee I'd love to hear about it.  Has anyone in this forum already integrated Boxee into their Mythbuntu setup?

EDIT: I guess I should include a link to the website. [Click Here]("http://www.boxee.tv")

---

### Post by Stevi on 2008-11-12
Sounds really interesting!
> **Meph1st0 said:**
> Could this be an additional Mythtv plugin to include boxee service? 
Yeah, a mythtv plugin would be great!

---

### Post by penbrock on 2008-11-21
I am just starting to play with Mythbuntu. I don't even have it connected to the TV feed yet but love it.
It seems to me that sites like Hulu would be a GREAT add-on to MythTV. Heck I could almost disconnect my cable TV if I had fast/easy access to it's web based shows. Maybe in a [Watch IP_TV] option like the [Watch TV] and find some way to program "channels"

Not being a programmer I know this sounds easy but I am sure it is not.

---

### Post by Meph1st0 on 2008-11-21
I too think this would be a great plugin for mythbuntu.  In fact, I had previously made a post asking the same questions.  [http://ubuntuforums.org/showthread.php?t=979938](http://ubuntuforums.org/showthread.php?t=979938)

If I were smart enough and had the time, I think it'd be fun to create a Boxee plugin.  Unfortunately the "smart enough" part is the big killer.

---

### Post by tgm4883 on 2008-11-21
There is work being done to make this happen, but it doesn't look promising.  Not saying it can't be done, but it probably won't be done officially unless we get to go ahead from hulu.com (and other sites as well).  

We do have an email in to them though asking permission.  If that gets approved then work will begin on it, but I wouldn't plan on it making it into 9.04.  If any community member would like to work on that though go right ahead.

---

### Post by Cyberai on 2008-11-24
I played with this a few weeks ago. I basically just went and found the shows I wanted to keep tabs on at HULU and created a HULU menu entry in my TV menu. I pointed that entry to a new HULU menu I wrote that have individual entries defined that pointed to each show with an "exec firefox <show URL>" in the action line. 

That gave me a basically functional setup. I had to use the keyboard/mouse to put the HULU embedded flash player into full screen mode and to quit out of FF afterwards. 

Integrating ANY of the new P2P TV web services would really be pretty trivial. All that would be needed would be code to parse the RSS feeds for the pages and create a menu. I guess you would also have to automate the switch to full screen mode. Last thing would be LIRC integration, but that's not hard.

I'd do this myself, but I'm under too much pressure at work to devote any time to side projects right now. Perhaps someone can take the technique I described and play it out.

---

### Post by foxbuntu on 2008-11-24
> **tgm4883 said:**
> There is work being done to make this happen, but it doesn't look promising.  Not saying it can't be done, but it probably won't be done officially unless we get to go ahead from hulu.com (and other sites as well).  

We do have an email in to them though asking permission.  If that gets approved then work will begin on it, but I wouldn't plan on it making it into 9.04.  If any community member would like to work on that though go right ahead.

I want to make it very clear that the only software that will be packaged and supported by the Mythbuntu team will have to be legit. Nothing that breaks any website's Terms of Service agreements or any laws.

---

### Post by dsauter on 2008-12-14
Using the following, I now access Boxee from MythTV via my remote.  When I close Boxee, I'm right back with MythTV.  It's very much like how Xine is accessed if you use it for DVD and video playback.

I highly recommend this to integrate Boxee with your Mythtv setup.  Kudos to misterjamin in the boxee forum.



taken from:  [http://forum.boxee.tv/showpost.php?p=15661&postcount=14]("http://forum.boxee.tv/showpost.php?p=15661&postcount=14")

> You could always customise your MythTV Menus? I added Boxee under the "Watch TV" link:

Code:

<button>
    <type>MENU_MEDIA_LIBRARY</type>
    <text>Boxee</text>
    <action>EXEC /home/mythtv/boxee-source-0.9.3921/Boxee</action>
</button>


Mine actually looked like this:

   <button>
    <type>MENU_MEDIA_LIBRARY</type>
    <text>Boxee</text>
    <action>EXEC /opt/boxee/run-boxee-desktop</action>
   </button>

and I found the appropriate file at:
/usr/share/mythtv/themes/Mepo-wide/mainmenu.xml
of course, that's not a stock Mythbuntu theme, so you will have to look to find your own mainmenu.xml, presumably somewhere in /usr/share/mythtv/themes/.

---

### Post by bmathis on 2008-12-14
This is awesome news... im going to try to get it working later today. Ill report back if I can get it working!

**UPDATE

I am running MythBuntu 64bit and boxee doesn't currently work with 64bit, so its a no go for me :`(

---

### Post by dakota34 on 2008-12-14
Boxee is a port of XBMC with a focus on the 'social' aspect of the fabulous XBMC media center. XBMC for linux, which uses Ubuntu as it's target distro, is a fantastic front-end for all types of media. Myth-tv integration exists in a limited manner already, and fuller integration is being worked on, extending a GSOC project...

Many people incorporate XBMC into their Myth frontend using the technique outlined in the previous post for boxee ... I find XBMC's automatic meta-data collection function, which incorporates fan art and a really impressive 'episodes' view for tv, to be incredible, and I find myself watching my movies through xbmc more and more (as opposed to mythvideo) because it's just, well, nicer. It's hard to explain, but if you try it you'll see what I mean. 

I'd urge anyone who's interested in seeing a cutting edge visual interface to give XBMC a whirl, there's UBUNTU PPA's on their website!

---

### Post by ares01590 on 2008-12-26
I also run amd64 ubuntu, but i found this thread which allowed me to install boxee and run it from mythfrontend as described here.

Here's the link:

[http://forum.boxee.tv/showpost.php?p=22698&postcount=20](http://forum.boxee.tv/showpost.php?p=22698&postcount=20)

It worked quite well, even in my diskless client image.

Boxee works pretty well, though it seems playing something from hulu sometimes causes it to refuse to exit -- requiring a "kill -9" to get back to Myth.  I've had no problem with apple trailers, cbs, or comedy central.  not a lot of testing yet, however.

My frontend can't handle the OpenGL demands for HD 720p, however.  Its just got Nvidia 6150LE on board graphics.

David.

---

### Post by BadServo on 2008-12-27
> Mine actually looked like this:

<button>
<type>MENU_MEDIA_LIBRARY</type>
<text>Boxee</text>
<action>EXEC /opt/boxee/run-boxee-desktop</action>
</button>

I tried this on my Mythbuntu 8.10 installation with the latest Boxee Linux Alpha.  The file I modified was /usr/share/mythtv/mainmenu.xml.

The button now shows up, but when I select it, the screen just flickers then fails.  If I exit MythTV and run Boxee from the menu it fires right up.  So run-boxee-desktop is definitely the right command.

Any help would be appreciated.

---

### Post by bawilson2 on 2009-01-08
> **dsauter said:**
> Using the following, I now access Boxee from MythTV via my remote.  When I close Boxee, I'm right back with MythTV.  It's very much like how Xine is accessed if you use it for DVD and video playback.

I highly recommend this to integrate Boxee with your Mythtv setup.  Kudos to misterjamin in the boxee forum.



taken from:  [http://forum.boxee.tv/showpost.php?p=15661&postcount=14]("http://forum.boxee.tv/showpost.php?p=15661&postcount=14")




Mine actually looked like this:

   <button>
    <type>MENU_MEDIA_LIBRARY</type>
    <text>Boxee</text>
    <action>EXEC /opt/boxee/run-boxee-desktop</action>
   </button>

and I found the appropriate file at:
/usr/share/mythtv/themes/Mepo-wide/mainmenu.xml
of course, that's not a stock Mythbuntu theme, so you will have to look to find your own mainmenu.xml, presumably somewhere in /usr/share/mythtv/themes/.

I used this tag in my /usr/share/mythtv/mainmenu.xml and things worked out great.  Boxee is a pretty cool program.  It is also nice that they just opened up access to all Linux and Mac users.  Windows users still need to wait for an invitation.

---

### Post by wizgnome on 2009-05-10
WOW!:popcorn:

Just found this application, added it to my mainmenu.xml (having just upgraded to 9.04) and now I can access all sorts of online content - YouTube, Apple Movie Trialers, Shoutcast Radio and loads more, all full screen and controlled with my remote control. Seems to have all the things missing from MythTV.

I could not get it to access my mytv database, but not to bothered as I have that already on the TV menu!!!:)

---

### Post by iitywygms on 2009-05-19
Mythbuntu + Boxee = Heaven.

---

### Post by urvaius on 2009-05-29
just set this up. works Great!!!

---

### Post by penbrock on 2009-05-29
I know I should be posting this in the Boxee forums but I can not get an answer there and was hoping one of you could help me out. I have MythTV running fine, and  Boxee runs how ever I can not get Boxee to see my Hauppauge WinTV-Go remote.
If anyone has gotten their remote working can you please send me an email with what you changed?

Thank you, I am dieing to get this working
[EMAIL="penbrock@penbrock.com"]penbrock@penbrock.com[/EMAIL]

---

