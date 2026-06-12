---
title: "Integrating Google+ Hangouts and Mythtv"
date: 2011-11-06
forum: Mythbuntu
---

### Post by dfacto on 2011-11-06
Here is the necessary code to make Google+ more app-like, for purpose of integrating with Mythtv.

Sorry I don't have time to properly explain all of this, but if you have a basic understanding of *nix and Mythtv you should be able to set it up.

App-ify Google+: [google-hangout]("http://almostsure.com/google-hangout/google-hangout")

Simple Lirc configuration: [.lirc/google-hangout]("http://almostsure.com/google-hangout/dotlirc_google-hangout")

Control webcam: [webcam]("http://almostsure.com/google-hangout/webcam")

Library.xml entry:
```

    <button>
        <type>TV_SEARCH_NEW_TITLES</type>
        <text>Hangout on Google+</text>
        <action>EXEC /path/to/google-hangout</action>
    </button>

```


The google-hangout script assumes a specific name of the Hangout.  You will probably want to change this to something that you and your friends agree on using.  Alternatively, one could make a mythtv sub-menu that has all of the named hangouts you use. 

The lirc config file uses right and left as tab and shift+tab and up/down as up/down with "OK" mapped to "Enter".  We find these the most important.  It is also nice to set-up zoom and F11 (full-screen). It also maps the keypad to the camera controls:
[LIST=1]
[*]zoom out
[*]tilt up 
[*]zoom in
[*]pan left
[*]reset
[*]pan right
[*]--
[*]tilt down
[*]--
[/LIST]
On the remote this is a bit more intuitive since it is organized as:
   1 2 3
   4 5 6
   7 8 9

The webcam script just uses "digital" controls which UVC does indeed support...at least for the [Logitech HD Pro Webcam C910]("http://www.amazon.com/Logitech-1080p-Webcam-C910-Skype/dp/B003M2YT96/").

Let me know if you have ideas for tweaks!

**Update**: I added a web interface to the simple webcam script which allows people to remotely reposition the camera.
[index.html]("http://almostsure.com/google-hangout/index-html")
[webcam.cgi]("http://almostsure.com/google-hangout/webcam-cgi")
It isn't pretty looking, but it is fairly functional (it doesn't have a page refresh at every click at least).

---

