---
title: "The latest Spotify: Connecting to Facebook issue"
date: 2010-04-28
forum: Multimedia Software
---

### Post by beerskij on 2010-04-28
The latest version of Spotify incorporates a social networking part, which allows you to connect with your friends to share playlists etc.

However, accessing this feature using Ubuntu and running Spotify with Wine isn't the easiest thing to do.

Regular Spotify works well, but I cannot login to my Facebook account. Apparantly, this is due to that part of Spotify using IE7 components.

I couldn't get past the diaglogue box asking me to enter usr/pass, but after some googling I got IE7 support for Wine running using Winetricks. Now I can log in, but I get stuck at another point: the window where I'm to accept that Spotify accesses my private information. I click OK but then it just stands still, loading, and nothing happens.

I know the new version just came out, but has anybody got any idea of how to fix it? Perhaps adding some other stuff with Winetricks beside IE7 support?

---

### Post by guriinii on 2010-04-28
I had the same problem, I did this:```
wine iexplore http://www.winehq.org
```
Then follow the prompts.

---

### Post by beerskij on 2010-04-28
I tried it, but only recieve an error message (iexplore.exe crashed unexpectedly).

However, looking at the appdb at winehq:

**What works**

Mostly everything I've tried so far.
   
[LIST]
[*]Most functions from 3.1.3 works as expected
[*]Facebook integration works (as far as I've tested)
[*]Social profiles works
[/LIST]
This was tested on Jaunty and Karmic. I am, however, using Lucid. Perhaps that's the issue.

---

### Post by kostkon on 2010-04-28
Try installing the package
```
wine1.2-gecko
```
(assuming that you are using *wine1.2*, as you should).

---

### Post by mikaelbj on 2010-04-28
I'm also having problems connecting Spotify with Facebook on my Lucid 10.04 install. I am just being thrown back at the login page saying "You must log in to see this page" after attempting to log in. wine1.2-geck is installed.

---

### Post by Aurdal on 2010-04-28
Steps to getting this working:
1. Install IE7 with winetricks.
2. In IE7 set security to "medium" instead of the default "medium-high". (You can change this back afterwards.)
3. Login to Facebook with Spotify and click allow.

If you get the IE crash message, run it with the following command:
```
wine ~/.wine/dosdevices/c:/Program\ Files/Internet\ Explorer/iexplore.exe
```

---

### Post by Jumpingmushroom on 2010-04-29
I've managed to get to the point where I can log into Facebook with Spotify, but after that it simply says "Friends import cancelled" and wants me to either try again, or try later. This might of course be something with facebook, but I find that kind of strange.

---

### Post by mikaelbj on 2010-04-29
> **Aurdal said:**
> Steps to getting this working:
1. Install IE7 with winetricks.
2. In IE7 set security to "medium" instead of the default "medium-high". (You can change this back afterwards.)
3. Login to Facebook with Spotify and click allow.

If you get the IE crash message, run it with the following command:
```
wine ~/.wine/dosdevices/c:/Program\ Files/Internet\ Explorer/iexplore.exe
```

This solved my problem. Takk/thanks!

---

### Post by apakatt on 2010-05-01
Nothing of the above solutions worked for me but I noticed that you can sign in to your Spotify account on a Windows (or OS X i guess) machine and create the Spotify-Facebook-connection working there. Since it's stored remotly on the Spotify server, you're now able to start Spotify via Wine and the connection is still there.

---

### Post by ukblacknight on 2010-05-01
I had this problem too, I had to open up Windows 7 in a VM and connect that way.

Unfortunately, I can't get Spotify to play anything now though!  No songs will play :(

---

### Post by jacoborus on 2010-05-01
1. Go to [www.spotify.com](www.spotify.com) and login
2. click here: [https://www.spotify.com/en/account/social/facebook/]("https://www.spotify.com/en/account/social/facebook/")

3. Run Spotify & enjoy

---

### Post by LarsEriksson on 2010-05-03
> **jacoborus said:**
> 1. Go to [www.spotify.com](www.spotify.com) and login
2. click here: [https://www.spotify.com/en/account/social/facebook/]("https://www.spotify.com/en/account/social/facebook/")

3. Run Spotify & enjoy


Worked perfectly, thanks a bunch :)

---

### Post by stolsvik on 2010-05-03
> **Aurdal said:**
> Steps to getting this working:
1. Install IE7 with winetricks.
2. In IE7 set security to "medium" instead of the default "medium-high". (You can change this back afterwards.)
3. Login to Facebook with Spotify and click allow.


This solved my problem too, but I had installed Spotify using PlayOnLinux. I had to set the following...:```
export WINEPREFIX=/home/endre/.PlayOnLinux/wineprefix/Spotify
```
... before running winetricks ie7. Thus the IE7 was installed into the same prefix as Spotify, and I assume it then was used when logging into facebook. (I had some problems with the mouse pointer disappearing when I hit input fields in the facebook login page within Spotify, but by a little trial and error, I managed..)

---

### Post by JohnJackson on 2010-05-06
> **jacoborus said:**
> 1. Go to [www.spotify.com](www.spotify.com) and login
2. click here: [https://www.spotify.com/en/account/social/facebook/]("https://www.spotify.com/en/account/social/facebook/")

3. Run Spotify & enjoy

Thanks, did the trick for me.

---

### Post by oooh on 2010-05-15
> **jacoborus said:**
> 1. Go to [www.spotify.com](www.spotify.com) and login
2. click here: [https://www.spotify.com/en/account/social/facebook/]("https://www.spotify.com/en/account/social/facebook/")

3. Run Spotify & enjoy


That worked perfect on mine

However, it started crashing randomly while playing music

Anybody had this problem ?

---

### Post by jacoborus on 2010-05-20
> **oooh said:**
> 

However, it started crashing randomly while playing music

Anybody had this problem ?

Yes, but just in Ubuntu Karmic, I solved this typing in terminal:

```
sudo aptitude install wine1.2
```

---

### Post by Lundefuglen on 2011-04-26
Hi,
I have a similar problem, only nothing happens when I link it. Spotify says "Sucess" when I've loaded my Facebook-profile, but no friends is on the list...
The links over didn't work btw..
Thanks

---

### Post by anthonyvo on 2011-11-03
> **jacoborus said:**
> 1. Go to [www.spotify.com]("http://www.spotify.com") and login
2. click here: [https://www.spotify.com/en/account/social/facebook/](https://www.spotify.com/en/account/social/facebook/)

3. Run Spotify & enjoy

This worked for me.

---

### Post by Jesuswashomeless on 2011-11-10
> **anthonyvo said:**
> This worked for me.

I tried this but it just sends me to a page that says 
"Sorry there has been a temporary error, please try again later."
Any advice? 
I have spotify running all right in Wine as long as I disable the app from face book first, but I would really like to be able to use it in conjunction with facebook.

Sorry I have tried to delete this as I am just learning to post and quoted the wrong reply but I couldn't.

---

### Post by Jesuswashomeless on 2011-11-10
> **jacoborus said:**
> 1. Go to [www.spotify.com](www.spotify.com) and login
2. click here: [https://www.spotify.com/en/account/social/facebook/]("https://www.spotify.com/en/account/social/facebook/")

3. Run Spotify & enjoy

I tried this but it just sends me to a page that says 
"Sorry there has been a temporary error, please try again later."
Any advice? 
I have spotify running all right in Wine as long as I disable the app from face book first, but I would really like to be able to use it in conjunction with facebook.

---

