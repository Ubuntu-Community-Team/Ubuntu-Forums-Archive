---
title: "Songbird font rendering (hinting)"
date: 2009-05-27
forum: Multimedia Software
---

### Post by Tux0Racer on 2009-05-27
For some reason I can't turn off hinting in Songbird on Ubuntu. I turned off hinting in the Appearance settings for Gnome and also setup a .fonts.conf with the following:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

<match target="font">
	<edit mode="assign" name="hintstyle">
		<const>hintnone</const>
	</edit>
</match>
</fontconfig>

```

All applications respect this setting except Songbird. Even if I turn anti-aliasing off altogether Songbird seems to do its own thing with fonts.

---

### Post by jimbo99 on 2009-05-27
I don't doubt that as I don't think Songbird is really a native Linux app.  It doesn't follow other interface guidelines either, and as such it restricts movement of the window outside of the borders of the desktop (at least the last time I looked at it).  I looked at it and thought, hmmm, this looks like a wine app.

I just downloaded it again and installed.  Nah, this isn't a native Linux app.  They are gimmicking it by folding it into something other than true linux.  No, it isn't a valid question to ask "what is a native Linux app" as we all know what one is.

I might suggest you look into Exaile as a replacement for Songbird.

---

### Post by Tux0Racer on 2009-05-27
Thanks for the reply, however you are mistaken. Songbird is indeed a native Linux app.

---

### Post by orange-wedge on 2009-05-27
Have you tried installing the latest version of songbird from their site?  I know that the repository sometimes was not exactly up-to-date when 1.1 came out.

---

### Post by jimbo99 on 2009-05-28
Actually, Songbird is NOT a native Linux app.  You can see this by looking at the screen elements.  It's a mash up, but certainly it is NOT a native Linux app.

---

### Post by Tux0Racer on 2009-05-28
> **jimbo99 said:**
> Actually, Songbird is NOT a native Linux app.  You can see this by looking at the screen elements.  It's a mash up, but certainly it is NOT a native Linux app.

You're absolutely wrong about this. You can download the source code and compile it on your linux box yourself.

I'm fairly new to the Ubuntu forums. Is this seriously the level of discourse here? "It's not a native app you can tell by looking at the 'screen elements'"? Are you for real?

ANYWAYS, if anyone has any insight on the font rendering issue that would be great! I know Songbird uses fontconfig and gtk so I can't see why it wouldn't respect the .fonts.conf settings. I've heard they use a hacky version of xulrunner. Maybe that's the issue?

---

### Post by Tux0Racer on 2009-05-28
> **orange-wedge said:**
> Have you tried installing the latest version of songbird from their site?  I know that the repository sometimes was not exactly up-to-date when 1.1 came out.

Thanks for the tip. I tried a nightly but experienced the same issue.

---

### Post by Tux0Racer on 2009-12-22
For anyone else who comes across this: It looks like the issue is that the Songbird team does not compile with --enable-system-cairo

Until that bug is fixed you're forced to manually recompile with --enable-system-cairo

Although I get the impression that Songbird is quick becoming a second class citizen on Linux so it may be better to save yourself the aggravation is simply use Banshee.

---

