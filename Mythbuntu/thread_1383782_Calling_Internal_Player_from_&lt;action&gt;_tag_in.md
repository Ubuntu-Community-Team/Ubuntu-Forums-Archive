---
title: "Calling Internal Player from &lt;action&gt; tag in xml&#8207;"
date: 2010-01-17
forum: Mythbuntu
---

### Post by bbruenfl on 2010-01-17
I am attempting to configure the mythbuntu-apple-trailers plugin to run on my mythtv setup and have run into a snag.  The peculiarities of my box disable the sound from all other sources when the mythfrontend is running leaving me with either using the Internal player exclusively or trying to solve a sound driver problem.  In pursuit of the former, I am attempting to discover a way to call the Internal player from an <action> tag in appletrailer.xml.  The format for the plug in is...
```

<mythmenu name="TRAILERS">
        <button>
                <type>VIDEO_BROWSER</type>
                <text>The Most Dangerous Man In America</text>
                <action>EXEC /usr/bin/mplayer -fs -zoom -really-quiet /var/lib/mythtv/trailers/mostdangerousmaninamerica_h320.mov</action>
        </button>
</mythmenu>

```So the question is is there a CLI for the internal player or is there an action tag that will call the internal player.  If the later, what params should be passed?

Cheers,
Bo

---

