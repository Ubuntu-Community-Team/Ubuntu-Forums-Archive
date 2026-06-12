---
title: "Spotify Free without WINE"
date: 2011-12-07
forum: Multimedia Software
---

### Post by hitman_dreams on 2011-12-07
If this has been done, please let me know and I'll take this down.

This will allow you to install and run Spotify Free in Ubuntu (for those of us who don't feel like paying $120/yr for music you don't get to keep). Basically we are installing the Linux version and modifying it to work for free users.

[B][SIZE="3"]Open the sources.list for editing:[/SIZE]
[/B]
[COLOR="Olive"]sudo gedit /etc/apt/sources.list[/COLOR]

You can replace "gedit" with whatever editor you prefer to use.

**[SIZE="3"]At the bottom of that file add:[/SIZE]**

[COLOR="olive"]deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free[/COLOR]

then save and exit.

**[SIZE="3"]Add the public key:[/SIZE]**

[COLOR="olive"]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E[/COLOR]

**[SIZE="3"]Run apt-get update:[/SIZE]**

[COLOR="olive"]sudo apt-get update[/COLOR]

**[SIZE="3"]Install:[/SIZE]**

[COLOR="olive"]sudo apt-get install spotify-client-qt[/COLOR]

That should do it. If you get errors in any step, fix it before moving on. Once you get it installed and to the point where it opens, continue below.



**[SIZE="3"]In the terminal run the following:[/SIZE]**

[COLOR="olive"]gconftool-2 -t string -s /desktop/gnome/url-handlers/spotify/command \ “$HOME/bin/openspotify %s”[/COLOR]

[COLOR="olive"]gconftool-2 -t bool -s /desktop/gnome/url-handlers/spotify/needs_terminal false[/COLOR]

[COLOR="olive"]gconftool-2 -t bool -s /desktop/gnome/url-handlers/spotify/enabled true[/COLOR]

You're all set. Enjoy Spotify Free without WINE! :guitar:

---

### Post by antpruitt on 2011-12-31
yeah unfortunately, this just crashes for me still on 11.10.

Spotify launches, and then just disappears/closes after about 7 seconds.  :(

---

### Post by jofsson on 2012-01-02
> **hitman_dreams said:**
> If this has been done, please let me know and I'll take this down.

This will allow you to install and run Spotify Free in Ubuntu (for those of us who don't feel like paying $120/yr for music you don't get to keep). Basically we are installing the Linux version and modifying it to work for free users.

[B][SIZE="3"]Open the sources.list for editing:[/SIZE]
[/B]
[COLOR="Olive"]sudo gedit /etc/apt/sources.list[/COLOR]

You can replace "gedit" with whatever editor you prefer to use.

**[SIZE="3"]At the bottom of that file add:[/SIZE]**

[COLOR="olive"]deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free[/COLOR]

then save and exit.

**[SIZE="3"]Add the public key:[/SIZE]**

[COLOR="olive"]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E[/COLOR]

**[SIZE="3"]Run apt-get update:[/SIZE]**

[COLOR="olive"]sudo apt-get update[/COLOR]

**[SIZE="3"]Install:[/SIZE]**

[COLOR="olive"]sudo apt-get install spotify-client-qt[/COLOR]

That should do it. If you get errors in any step, fix it before moving on. Once you get it installed and to the point where it opens, continue below.



**[SIZE="3"]In the terminal run the following:[/SIZE]**

[COLOR="olive"]gconftool-2 -t string -s /desktop/gnome/url-handlers/spotify/command \ “$HOME/bin/openspotify %s”[/COLOR]

[COLOR="olive"]gconftool-2 -t bool -s /desktop/gnome/url-handlers/spotify/needs_terminal false[/COLOR]

[COLOR="olive"]gconftool-2 -t bool -s /desktop/gnome/url-handlers/spotify/enabled true[/COLOR]

You're all set. Enjoy Spotify Free without WINE! :guitar:


Works great! Thanks alot!

---

### Post by yugnip on 2012-01-02
> **antpruitt said:**
> yeah unfortunately, this just crashes for me still on 11.10.

Spotify launches, and then just disappears/closes after about 7 seconds.  :(

Try cleaning out the .cache/spotify folder.

---

### Post by I_can_see_the_light on 2012-01-02
> **hitman_dreams said:**
> [COLOR="olive"]gconftool-2 -t string -s /desktop/gnome/url-handlers/spotify/command \ “$HOME/bin/openspotify %s”[/COLOR]
What's inside the **openspotify** script?

---

### Post by garfieldpbj on 2012-01-04
> **hitman_dreams said:**
> 
**[SIZE="3"]In the terminal run the following:[/SIZE]**

[COLOR="olive"]gconftool-2 -t string -s /desktop/gnome/url-handlers/spotify/command \ “$HOME/bin/openspotify %s”[/COLOR]

[COLOR="olive"]gconftool-2 -t bool -s /desktop/gnome/url-handlers/spotify/needs_terminal false[/COLOR]

[COLOR="olive"]gconftool-2 -t bool -s /desktop/gnome/url-handlers/spotify/enabled true[/COLOR]



Why do this?

/Peter

---

### Post by marco123 on 2012-05-27
Works perfectly and streams smoothly with normal or high quality streaming.

Thank you very much for the easy step by step instructions! :popcorn:

---

### Post by slavssn on 2012-05-27
Now there's also an *official* way of installing Spotify, check this out:
[http://www.spotify.com/se/download/previews/](http://www.spotify.com/se/download/previews/)
> **Debian**
# 1. Add this line to your list of repositories by
#    editing your /etc/apt/sources.list
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free

# 2. If you want to verify the downloaded packages,
#    you will need to add our public key
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E

# 3. Run apt-get update
sudo apt-get update

# 4. Install spotify!
sudo apt-get install spotify-client**[COLOR="Red"]*[/COLOR]**
**[COLOR="Red"]*[/COLOR]** - to start the client, you need to start **spotify** instead of **spotify-client**

Worked like a charm on both Lubuntu 11.10 and 12.04. A friend of mine, who is Swedish, created an account for me so I could check it out, and I have to say it's a brilliant application. Sadly, it detected that I was logging in from Poland and blocked my account after a couple of weeks.

---

### Post by jpeddicord on 2012-05-27
I just want to state here that these are legitimate instructions, and are also available on the Spotify website as the previous poster stated.

---

### Post by aaronszone1 on 2012-05-31
There is a way to get spotify free and install it without the command line.  Go to the spotify repository here: [http://repository.spotify.com/pool/non-free/s/spotify/](http://repository.spotify.com/pool/non-free/s/spotify/)

Download the appropriate version then install with the Ubuntu Software Center.

Done.

Enjoy :)

---

