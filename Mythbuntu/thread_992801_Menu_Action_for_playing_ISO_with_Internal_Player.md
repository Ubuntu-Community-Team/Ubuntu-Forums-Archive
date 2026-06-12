---
title: "Menu Action for playing ISO with Internal Player?"
date: 2008-11-25
forum: Mythbuntu
---

### Post by Lindsay.Mathieson on 2008-11-25
I need to play a ripped DVD ISO using the internal player via a custom menu action, however I can't find any myth menu actions for launching the internal player with a specific file.

Does anyone know of any?

Thanks,

Lindsay

---

### Post by ahood on 2008-11-25
> **Lindsay.Mathieson said:**
> I need to play a ripped DVD ISO using the internal player via a custom menu action, however I can't find any myth menu actions for launching the internal player with a specific file.

Does anyone know of any?

Thanks,

Lindsay

Hello,

Will any of the solutions described below work?

[LIST=1]
[*]Import the ISO file into the MythTV database so that it can be played with the existing menu (Home/Main --> Media Library --> Watch Videos)

[*]Exiting out of the frontend and execute a command that plays the ISO file.

[*]Exiting out of the frontend and launch VLC or Xine that will play the ISO file.
[/LIST]

If not, a bit more information would go a long way.

For instance,

[LIST]
[*]Was the MythTV DVD rip utility used to create the iso file?

[*]Where is the iso file located?

[*]Is VLC or Xine installed (see Mythbuntu Control Center)?
[/LIST]I hope the above helps.

---

### Post by Lindsay.Mathieson on 2008-11-25
Thanks ahood, it good to know there's no built in solution.

I ripped the DVD using Myth and it is imported and playable via the video module.

What I was hoping to do was have dedicated entries in the Myth Menu to make things easier for my wife, she's not entirely comfortable with navigating the video manager. Its just two exercise DVD's she'd like to play on a regular basis - a WAF thing basically :)

I've had reasonable success using Xine
```

<mythmenu name="LOUISE">
	<button>
		<type>VIDEO</type>
		<text>Pilates Tone Up</text>
		<action>EXEC xine -pfh -A alsa -I --no-splash --fullscreen "dvd://var/lib/mythtv/videos/Louise/Total Tone Up.iso"</action>
	</button>
</mythmenu>

```
Just have to tweak lirc a bit and for some reason the volume control is not working. I would have prefered to use the internal player as its better integrated, but not to be :)

---

