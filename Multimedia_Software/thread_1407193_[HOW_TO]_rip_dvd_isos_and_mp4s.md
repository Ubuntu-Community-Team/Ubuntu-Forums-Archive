---
title: "[HOW TO] rip dvd isos and mp4s"
date: 2010-02-15
forum: Multimedia Software
---

### Post by Gryphen on 2010-02-15
Before you can rip dvds on ubuntu you have to get the medibuntu repository.
To add the medibuntu repository, open the terminal and paste in ```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```Now install the required codecs ```
sudo apt-get install libdvdcss2 non-free-codecs
```And download install handbrake [http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php).

Now the dvd copying process,
Use brasero or k3b to copy the dvd.
In brasero click "disc copy" then under "select a disc to write to" select "image file".
In k3b go to tools>copy medium click "only create image" then in the image tab chose a temporary directory where you want you iso to go. You can use vlc to play the iso, but iso should about 7.5 gb which takes up alot of space. So now we're going to use handbrake to transcode the movie to a much smaller size(1.5gb). Open handbrake select your preset(I use "high profile") then select source then your iso now click start. If you want to add more isos select the new iso but click "add to queue"

 The reason we copied isos instead of just using handbrake is because it's much faster to copy the the iso than to transcode the movie. And you can keep copying isos while handbrake is transcoding the and add the newly copied dvd isos to the queue while handbrakes going.

Some of the newer dvds have 99 titles, most of them(all of them except the bonus features) are scrambled(I.E. random chapter order) versions of the movie. So if you want to know the right title you have to open the dvd in vlc, play the movie then when the actual movie is playing(make sure the box in the lower right corner shows a duration that looks like the main feature.) look in Playback>Title and the title will be checked

---

