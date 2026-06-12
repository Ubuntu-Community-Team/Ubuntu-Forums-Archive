---
title: "Amazon Music Downloads"
date: 2015-03-29
forum: Multimedia Software
---

### Post by ozark_hillbilly on 2015-03-29
I have been using Clamz MP-3 Downloader with great success for getting albums off of Amazon.com. Clamz uses the .amz file put on your Downloads folder by Amazon when you invoke the  "download your music" option. It then converts the music and places it in the user's music folder under the artist sub folder. That works fine.

Here's where I have some difficulty:

I purchased some CD albums and Amazon also gave me a free MP-3 download option of that music. When I go to my AmazonMusic area, under Library, it lists all the albums, including the latest they gave me for free after purchasing the CD's. I can't download the entire album in one fell swoop like when you purchase a MP-3 album. I can select up to 6 song tracks at a time and download those as a group. As it downloads the song(s) they show up on the Downloads folder as songxyz.mp3.crdownload during the download and then they automatically change to just songzyz.mp3 when the transfer is completed. I can play that song with Rhythmbox just fine. I can then move it to my music folder and play it from there just fine. But when I go to my Yamaha stereo network receiver, which is tied to my pc through Minidlna server, I cannot see the song. It displays [no content] on the receiver for that artist's sub folder. ??? The mp-3 file is there in the sub folder and set up identically to all the other music folder files from I can tell. 

This is not a problem because the CD's are enroute and I can just copy them over to my music folder once they arrive. But I don't understand why those single track mp-3 downloads off Amazon aren't visible to my network receiver. 

Anybody got an idea why this is so quirky,

ed

---

### Post by ozark_hillbilly on 2015-04-02
bump

---

### Post by Last_Ship on 2015-05-09
I've tried the solutions posted here and here [http://ubuntuforums.org/showthread.php?t=2269870&highlight=can%27t+amz+file](http://ubuntuforums.org/showthread.php?t=2269870&highlight=can%27t+amz+file) . Clamz used to work flawlessly for downloading Amazon music via the .amz file. The problem now is that first off, upon attempting to download a recently purchased album i receive the error "On Linux systems, your music library only supports downloading up to 6 songs at a time." It appears that this was overcome in the past by simply changing useragents to IE (or any other Windows-based useragent) and then Amazon would again provide the .amz file which could be opened in Clamz. 

Well now when I switch useragents Amazon *does *think I'm using IE10 in Windows; however, instead of giving me the .amz file it prompts me to download their app. I see that two people offered GreaseMonkey scripts in the past to overcome this, however, these scripts do not appear to be available anymore. I was able to successfully get Amazon's music installer running in Wine, but I wondered if anyone knew a trick to get the .amz file straight away and avoid having to use the Amazon Windows app.

---

