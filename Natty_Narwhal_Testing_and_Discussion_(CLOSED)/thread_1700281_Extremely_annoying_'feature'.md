---
title: "Extremely annoying 'feature'"
date: 2011-03-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2011-03-04
I have tolerated and even embraced all the big changes being made whilst others show a complete lack of faith in unity but it's the little things that make a good distro and I've just found one I used to enjoy has changed.

In windows if you call up a folder and then start typing the name of a file or folder it will take you to the nearest match in that folder. But if you don't type fast enough it will reset and forget what you were typing.

I have always preferred to use ubuntu for managing my files because I can type at a leisurely pace and still get the job done but tonight it's behaving like windows and deleting wat I have typed if I delay too long. This is an absolute pain in the neck!

---

### Post by ronacc on 2011-03-04
file a bug .

---

### Post by macroshaft on 2011-03-04
> **ronacc said:**
> file a bug .

Is it a bug though? Or by design?

---

### Post by ikt on 2011-03-04
> **macroshaft said:**
> deleting wat I have typed if I delay too long. This is an absolute pain in the neck!

I don't understand, what is being deleted if you delay for to long?

Are you saying that for example, if you type into dash:

Firef

and then sit on there for several seconds, Firef will be deleted? or that many of the results will be deleted the more you type into your search?

---

### Post by jocko on 2011-03-05
> **ikt said:**
> I don't understand, what is being deleted if you delay for to long?

Are you saying that for example, if you type into dash:

Firef

and then sit on there for several seconds, Firef will be deleted? or that many of the results will be deleted the more you type into your search?
He's talking about nautilus. Open up a nautilus window in a folder containing several files or folders, then start typing the beginning of the name of a file and it will become highlighted. As an example, if you open up your home folder and press "d" the desktop folder (first folder with a name starting with "d") will become highlighted, if you then press "o" before the function is reset, the documents folder (first file or folder with a name starting with "do") will get highlighted, and so on.
Apparently he thinks the function times out too quickly, so that pressing "d", then waiting for a while before pressing "o" will highlight a file starting with an "o" instead of "do"...

Any way, for me the timeout is about 6 seconds, which is more than enough...

---

### Post by Harry33 on 2011-03-05
> **macroshaft said:**
> Is it a bug though? Or by design?

I think this is not a bug in Nautilus, it is this by design.

---

### Post by mc4man on 2011-03-05
The 'timeout' is defined as 5, seems quite long enough. If you wanted to change then you'd need to rebuild nautilus - the define is in nautilus-2.32.2.1/libnautilus-private/nautilus-icon-container.c as here in blue
```
#define SNAP_CEIL_VERTICAL(y) SNAP_VERTICAL (ceil, y)

/* Copied from NautilusIconContainer */
#define NAUTILUS_ICON_CONTAINER_SEARCH_DIALOG_TIMEOUT [COLOR="Blue"]5[/COLOR]

/* Copied from NautilusFile */
#define UNDEFINED_TIME ((time_t) (-1))
```

---

### Post by macroshaft on 2011-03-05
> **jocko said:**
> 

Any way, for me the timeout is about 6 seconds, which is more than enough...

What I'm saying is that I have never known this feature to time out before. I have always had to press esc or click elsewhere in the window to get out of it. I much preferred it that way

---

### Post by macroshaft on 2011-03-05
Another issue that's starting to bug me is that they took away the icon bars at the top of the screen in firefox so I don't have a reload button any more. This was fine as I could use the reload located in the menus (view menu I think). Now they have removed that too so anyone with a broken F5 button on their laptop (like me) is simply stuffed!

---

### Post by kn0w-b1nary on 2011-03-05
> **macroshaft said:**
> Another issue that's starting to bug me is that they took away the icon bars at the top of the screen in firefox so I don't have a reload button any more. This was fine as I could use the reload located in the menus (view menu I think). Now they have removed that too so anyone with a broken F5 button on their laptop (like me) is simply stuffed!

Click View>Toolbars>Navigation Toolbar.

You can then right-click there>Customize, then drag and drop the buttons you want.

---

### Post by marshmallow1304 on 2011-03-05
> **macroshaft said:**
> Another issue that's starting to bug me is that they took away the icon bars at the top of the screen in firefox so I don't have a reload button any more. This was fine as I could use the reload located in the menus (view menu I think). Now they have removed that too so anyone with a broken F5 button on their laptop (like me) is simply stuffed!

Try View->Toolbars->Customize.  Ctrl+R should also work.

---

### Post by macroshaft on 2011-03-05
> **marshmallow1304 said:**
> Try View->Toolbars->Customize.  Ctrl+R should also work.

I forgot about ctrl + R but the customize option doesn't have reload in it, it has sync with what looks like a reload icon.

---

### Post by terry_gardener on 2011-03-05
> **macroshaft said:**
> Another issue that's starting to bug me is that they took away the icon bars at the top of the screen in firefox so I don't have a reload button any more. This was fine as I could use the reload located in the menus (view menu I think). Now they have removed that too so anyone with a broken F5 button on their laptop (like me) is simply stuffed!

at the right hand side of the URL there is a round arrow if you click this it reloads the page.

---

### Post by macroshaft on 2011-03-05
> **terry_gardener said:**
> at the right hand side of the URL there is a round arrow if you click this it reloads the page.

Got it! Ever heard the saying if it's not broken don't fix it? I stopped using windows because I got fed up with all the features moving and going through constant makeovers. You should never be able to lose something as simple as a reload button!

Thanks guys

---

### Post by cariboo on 2011-03-05
The reload button at the end of the url bar has been the default in firefox 4, since it was released, even before the globalmenu was added.

---

### Post by macroshaft on 2011-03-05
> **cariboo907 said:**
> The reload button at the end of the url bar has been the default in firefox 4, since it was released, even before the globalmenu was added.

Yes but that doesn't change the fact that I've been used to it being in the same place, in the same glaringly obvious styling for the past 15 years or so. I literally didn't notice it was there at all in ff4, it's so insignificant now.

---

### Post by jennybrew on 2011-03-05
> **cariboo907 said:**
> The reload button at the end of the url bar has been the default in firefox 4, since it was released, even before the globalmenu was added.

True.
Unfortunately it hides itself as an "x" until such time as one hovers the cursor over it. 
I think its quite difficult to notice. However ..familiarity eventually arrives :)

---

### Post by terry_gardener on 2011-03-05
> **jennybrew said:**
> True.
Unfortunately it hides itself as an "x" until such time as one hovers the cursor over it. 
I think its quite difficult to notice. However ..familiarity eventually arrives :)

it only changes to a X when a page is loading (so you can stop a page loading) when the page is done loading it changes to a round arrow, no matter where the cursor is.

---

### Post by EowynCarter on 2011-03-05
Hey, i didn't even knew nautilus could do this. 

You learn stuff every day.

---

### Post by jennybrew on 2011-03-05
> **terry_gardener said:**
> it only changes to a X when a page is loading (so you can stop a page loading) when the page is done loading it changes to a round arrow, no matter where the cursor is.

Not on my system it doesnt !
To be fair here I am having quite a lot of trouble with Firefox especially with it freezing.
Hopefully tomorrow will solve when I do a planned fresh install.

---

### Post by jennybrew on 2011-03-05
> **EowynCarter said:**
> Hey, i didn't even knew nautilus could do this. 

You learn stuff every day.

:p

---

### Post by cariboo on 2011-03-05
I admit I had to search for the firefox reload button the first time I used firefox 4, but once I found it, it seemed natural where it was, on that note, I only use firefox on my netbook, as the open in a browser option only works with firefox, I use chromium on a day to day basis on my desktop system.

---

### Post by macroshaft on 2011-03-05
> **cariboo907 said:**
> I admit I had to search for the firefox reload button the first time I used firefox 4, but once I found it, it seemed natural where it was, on that note, I only use firefox on my netbook, as the open in a browser option only works with firefox, I use chromium on a day to day basis on my desktop system.

Yes I agree, once you are aware of it the location seems very natural but I think because it's attached to the address bar you simply don't notice it the first time. It's so discreet that I would probably have remained blissfully unaware had nobody told me about it.

I think this is perhaps part of the recent obsession with trying to free up usable screen space. I have to wonder if it's going a bit far now. I did like having all my commands easily accessable from a toolbar and big enough to be used with my touchscreen. Oh well, that's progress!

---

### Post by bikeboy on 2011-03-05
The reload button can of course be moved to practically anywhere you like. Properly written addons can also be moved around in the addon bar, and you can choose to have the old-style menu or the new compact version. All in all, whether you like the changes or not (I like some and not others), much work has been done to make it more customisable than previously.

Re: the nautilus behaviour, it's the same here on Maverick so it's likely nothing has even changed. Perhaps the failure of the dialog to timeout for some people was a bug.

---

### Post by macroshaft on 2011-03-05
> **bikeboy said:**
> The reload button can of course be moved to practically anywhere you like. Properly written addons can also be moved around in the addon bar, and you can choose to have the old-style menu or the new compact version. All in all, whether you like the changes or not (I like some and not others), much work has been done to make it more customisable than previously.

Re: the nautilus behaviour, it's the same here on Maverick so it's likely nothing has even changed. Perhaps the failure of the dialog to timeout for some people was a bug.

I have to be honest I haven't tried to customise firefox at all. I can't really move a button I didn't know was there after all! And they are never going to be able to make changes we all agree are better.

As for the dialog timeout, can I have my bug back please?

---

### Post by cariboo on 2011-03-05
> **macroshaft said:**
> I have to be honest I haven't tried to customise firefox at all. I can't really move a button I didn't know was there after all! And they are never going to be able to make changes we all agree are better.

As for the dialog timeout, can I have my bug back please?

I seem to have the same problem, :) If I type the first letter of a directory, then wait a couple of seconds to type the second letter, the highlight is moved to a directory starting with the second letter I just typed. Is that what you are seeing?

---

### Post by macroshaft on 2011-03-05
> **cariboo907 said:**
> I seem to have the same problem, :) If I type the first letter of a directory, then wait a couple of seconds to type the second letter, the highlight is moved to a directory starting with the second letter I just typed. Is that what you are seeing?

Yes, the feature works fine if you type quickly, but if you are copying from something written down and lose your place, or if you get distracted by something then by the time you go to resume it has timed out and you have to start again. Windows works in exactly this way and it has always irritated me. I WILL DECIDE WHEN I HAVE FINISHED TYPING THANK YOU! I don't understand why this needs to time out ever.

---

### Post by mdurham on 2011-03-05
> **macroshaft said:**
> Yes, the feature works fine if you type quickly, but if you are copying from something written down and lose your place, or if you get distracted by something then by the time you go to resume it has timed out and you have to start again. Windows works in exactly this way and it has always irritated me. I WILL DECIDE WHEN I HAVE FINISHED TYPING THANK YOU! I don't understand why this needs to time out ever.
Unfortunately, like so many changes, it's change for changes sake.

---

### Post by macroshaft on 2011-03-05
> **mdurham said:**
> Unfortunately, like so many changes, it's change for changes sake.

I'm not certain it is change, perhaps it was a bug in previous versions. If so it's a bug I enjoyed and found enhanced my user experience.

---

### Post by mc4man on 2011-03-05
> I'm not certain it is change, perhaps it was a bug in previous versions. If so it's a bug I enjoyed and found enhanced my user experience.
The code involved in nautilus has been the same for quite some, at least from hardy (in hardy the value was 5000 though likely that meant milliseconds

Ubuntu isn't in the habit of changing upstream code too often, certainly not for something like this.

As mentioned if you don't like it change it, up or down

---

