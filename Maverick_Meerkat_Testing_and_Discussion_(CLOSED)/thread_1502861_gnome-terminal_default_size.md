---
title: "gnome-terminal default_size"
date: 2010-06-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by vigstrom on 2010-06-06
Hey, did I just dream that there were boxes for default size columns and rows in gnome-terminal profile preferences?

There are keys in gconf called default_size_rows and default_size_columns.

I had been wanting that along with the possibility to set default position for a long while. 
I know there are other ways to do that, command-line, compiz etc.

Maybe I'm confusing it with the gnome-panel applet SSHMenu. 
I'm otherwise very pleased with the changes in gnome-terminal.

---

### Post by wojox on 2010-06-06
Not that I can see in the Terminal App. I'm all updated as of fifteen minutes ago. Why would there be an option to set it to default size? 
It should always open at it's default size, unless you 've reconfigured it to open bigger or smaller. :)

---

### Post by vigstrom on 2010-06-06
> **wojox said:**
> Not that I can see in the Terminal App. Like I said, think I saw it in an earlier release. And there's the possibility to set cols and rows using gconf-editor. 

> **wojox said:**
>  I'm all updated as of fifteen minutes ago.  Yea, me to.

> **wojox said:**
> Why would there be an option to set it to default size?  There should be a possibility to set the window size (and position) PER PROFILE. It's useful.

> **wojox said:**
>  It should always open at it's default size, unless you 've reconfigured it to open bigger or smaller. :) Yes that's right, if I make it default, it should open at it's default size, but that's not what I mean. You should be able to set size (and position) per profile.

Now, I can of course first create a new profile and set most of the prefs in Profile Preferences, then start gconf-editor and set columns and rows there. 
But, I would much rather set all prefs in Profile Preferences.

:)

---

### Post by taavikko on 2010-06-06
> **wojox said:**
> Not that I can see in the Terminal App. I'm all updated as of fifteen minutes ago. Why would there be an option to set it to default size? 
It should always open at it's default size, unless you 've reconfigured it to open bigger or smaller. :)

In LL-version of gnome-terminal there indeed was an option in preferences to set the size of terminal, it got lost few updates ago...

I just like to launch the terminal via --geometry option
```
gnome-terminal --geometry=100x30
```

---

### Post by wojox on 2010-06-06
Double Post.

---

### Post by wojox on 2010-06-06
> **vigstrom said:**
> 
There should be a possibility to set the window size (and position) PER PROFILE. It's useful.

 Yes that's right, if I make it default, it should open at it's default size, but that's not what I mean. You should be able to set size (and position) per profile.

Now, I can of course first create a new profile and set most of the prefs in Profile Preferences, then start gconf-editor and set columns and rows there. 
But, I would much rather set all prefs in Profile Preferences.

:)

Okay I gotcha now. I never use Profiles so I forget all about them. :)


> **taavikko said:**
> In LL-version of gnome-terminal there indeed was an option in preferences to set the size of terminal, it got lost few updates ago...

I just like to launch the terminal via --geometry option
```
gnome-terminal --geometry=100x30
```

Yup. I forgot about the old --geometry. :)

---

### Post by hugmenot on 2010-08-18
The fields are back in the dialog now.

---

### Post by cariboo on 2010-08-18
it must be a gnome default, I just looked at PCLinuxOS 2010, and the columns and row settings are not there either.

---

