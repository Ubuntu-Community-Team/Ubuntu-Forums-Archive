---
title: "MythBuntu + XBMC Compatibility"
date: 2009-10-29
forum: Mythbuntu
---

### Post by Mattaus on 2009-10-29
Hi all,

Just a really quick question here as I'm pretty sure I know the answer,  but is there any reason I could not install XBMC under Mythbuntu?

Currently I run Ubuntu 9.04 which I set to auto launch MythTV on start up. On the main front end menu is a link that launches XBMC. I like this set up and would like to keep it that way but realise that using a full install of Ubuntu is a little bloated for what I am doing.

So I figure I can streamline the whole thing (and hopefully increase boot time and system stability) by installing Mythbuntu instead of Ubuntu.

So to repeat my initial question - are there any technical limitations preventing me from doing this? A quick search revealed a fair chunk of you do this sort of thing already, but I am unable to find specifics...

Having never used Mythbuntu (only MythTV) I am unsure if I have access to all the right tools - though I am confident I can run 90%of the things required from the command line.

Any validation of this 'theory' would be appreciated ;)

Cheers.

- Matt

---

### Post by nickrout on 2009-10-29
> **Mattaus said:**
> Hi all,

Just a really quick question here as I'm pretty sure I know the answer,  but is there any reason I could not install XBMC under Mythbuntu?

Currently I run Ubuntu 9.04 which I set to auto launch MythTV on start up. On the main front end menu is a link that launches XBMC. I like this set up and would like to keep it that way but realise that using a full install of Ubuntu is a little bloated for what I am doing.

So I figure I can streamline the whole thing (and hopefully increase boot time and system stability) by installing Mythbuntu instead of Ubuntu.

So to repeat my initial question - are there any technical limitations preventing me from doing this? A quick search revealed a fair chunk of you do this sort of thing already, but I am unable to find specifics...

Having never used Mythbuntu (only MythTV) I am unsure if I have access to all the right tools - though I am confident I can run 90%of the things required from the command line.

Any validation of this 'theory' would be appreciated ;)

Cheers.

- Matt

I run XBMC on a mythbuntu install. Its fine. 

I launch it from a custom menu entry. If you want details you can search the mailing list archives, or wait until I get home tonight :)

---

### Post by Mattaus on 2009-10-29
> **nickrout said:**
> 
I launch it from a custom menu entry. If you want details you can search the mailing list archives, or wait until I get home tonight :)


I do exactly the same thing at the moment. I guess I was jsut checking that Mythbuntu wasnt missing something XBMC needed, that Ubuntu had out of the box. Though I guess being Linux anything thats missing can just be added :D

Thanks for the reply, now that I know it works I'll put the effort of a rebuild in!

---

### Post by laffinet on 2009-10-29
> **nickrout said:**
> 
I launch it from a custom menu entry. If you want details you can search the mailing list archives, or wait until I get home tonight :)

Do you mind posting these details when you have a chance? Thanks.

---

### Post by kadafi69 on 2009-10-30
I do exactly this too, and it works perfectly.

you just need to create a new menu option under the main menu, I called mine XBMC. when selected it runs xbmc, leaving MythTV on in the background. When I close XBMC, MythTV comes back to the foreground. Works pretty seamlessly for me.

just enter this code into the mainmenu.xml file

<button>
<type>XBMC_CLIENT</type>
<text>XBMC</text>
<action>EXEC xbmc</action>
</button>

---

### Post by nickrout on 2009-10-30
> **kadafi69 said:**
> I do exactly this too, and it works perfectly.

you just need to create a new menu option under the main menu, I called mine XBMC. when selected it runs xbmc, leaving MythTV on in the background. When I close XBMC, MythTV comes back to the foreground. Works pretty seamlessly for me.

just enter this code into the mainmenu.xml file

<button>
<type>XBMC_CLIENT</type>
<text>XBMC</text>
<action>EXEC xbmc</action>
</button>

Dead right, same as mine.

HOWEVER don't do this to /usr/share/mythtv/mainmenu.xml, instead copy that file to ~/.mythtv.mainmenu.xml. Then edit that file. Then when you update mythtv it won't get overwritten.

---

