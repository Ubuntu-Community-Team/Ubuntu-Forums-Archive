---
title: "Mythtv Dependency Problems (libiec61883-dev)"
date: 2006-10-09
forum: Multimedia &amp; Video
---

### Post by drpepper on 2006-10-09
I've been following [THIS]("http://www.mythtv.org/wiki/index.php/Ubuntu_Dapper_Installation") guide over at mythtv.org

Everything has been fine, up untill actually installing, Mythtv. When following the install guide from source in the mythtv documentation, I check for dependencies with
[B]
apt-get build-dep mythtv[/B]

and it says it can't find the libiec61883-dev package. I have googled it and searched the forums but can't find where to get it from. 

Can anyone help, i really need this to work for a university project, and don't want to have to try another distro!

---

### Post by Osanya on 2006-10-10
were you trying to install MythTV 0.20?

I had the same problem. Myth 0.20 seems to have all sorts of dependency problems.

I installed 0.19 and it worked great.

If you've already got some myth packages installed, just uninstall them, update sources.list for 0.19 and re-install myth

should work fine.

---

### Post by drpepper on 2006-10-10
sounds like a plan! i've never uninstalled anything with apt....hmmm google time! are there any major differencies between 0.19 and 0.20?

cheers

---

### Post by Osanya on 2006-10-10
I haven't actually messed around with 0.20 but I've pretty much gotten 0.19 running the way I want. It was a lot of work in Ubuntu. If I were to do it again, I'd have used a different distro.

From what I've read, 0.20 has nuvexport integrated into the gui, so you can transcode to divx, xvid svcd, etc automatically. In 0.19 I had to seperately install nuvexport, compile ffmpeg enabeling xvid, mp3 etc, and then make a script that gets launched after every recording to cue up nuvexport and automatically transcode to xvid. It took a long time to get it working correctly... at least I think I have it working.

If anybody knows all the flags supported in nuvexport, I'd love to see them. That would have made things much easier. I can't find it documented anywhere.

---

