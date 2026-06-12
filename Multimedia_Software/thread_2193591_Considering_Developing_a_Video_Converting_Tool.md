---
title: "Considering Developing a Video Converting Tool"
date: 2013-12-13
forum: Multimedia Software
---

### Post by aytuggurbuz on 2013-12-13
I enjoy watching videos/movies on my PSVita. However, Sony decided they would require another format in order for their device to playback movies such that you cannot just copy your videos and watch them. God bless the people behind this idea!

On Windows I had a GUI program which successfully prepared my videos for the Vita, and it could even add subtitles. Quite enough for me.

On Linux, there is no such tool. Believe me I checked everywhere. However there is always the ffmpeg, which works most of the time, but there is no GUI for it. Trying to remember all the command line options is tedious.

Now I am here considering writing a Ruby GUI for ffmpeg, but I know close to nothing regarding all the codecs, formats, rates etc. I will need a full listing of all the options, and perhaps examples along with it. Then I can sit and write it. I could even distribute it to people having the same problem.

So please tell me what you think.

---

### Post by ajgreeny on 2013-12-13
What about **winff** which is a gui for ffmpeg?  I think you must have missed that, or perhaps it is not available from normal repos after 12.04, as ffmpeg is replaced by avconv.

---

### Post by aytuggurbuz on 2013-12-13
I had read somewhere that avconv doesn't support subtitles so I had to give up on it. Actually I had to compile ffmpeg from source in order to enable burning in subtitles.

It is strange that I have never come across winff. I have checked it now. It seems to want to use avconv by default. Is there a way I can switch it to ffmpeg instead?

---

### Post by ajgreeny on 2013-12-13
Sorry, no idea about that.

---

### Post by mc4man on 2013-12-13
> **aytuggurbuz said:**
> 

It is strange that I have never come across winff. I have checked it now. It seems to want to use avconv by default. Is there a way I can switch it to ffmpeg instead?
It will use which ever binary it comes first comes across, likely will default to avconv if both are present.
As far a using FFmpeg, winff uses presets, the repo version contains ones for libavcodec53 so you may  need to import newer ones or modify the existing one or create custom ones.
They have presets for libavcodec54 here, they could work to some extent if you have an FFmpeg binary that's at libavcodec55...
[http://code.google.com/p/winff/downloads/list](http://code.google.com/p/winff/downloads/list) about halfway down

(- Don't use any Ubuntu repo supplied FFmpeg binary, pure garbage

---

### Post by monkeybrain20122 on 2013-12-14
[https://launchpad.net/~samrog131/+archive/ppa](https://launchpad.net/~samrog131/+archive/ppa)

This comes with an up to date version of ffmpeg. It is installed in /opt, you can make it the default ffmpeg with the help to ffmpeg-set-alternatives (in  the ppa)
command:
sudo update-alternatives --config ffmpeg
Then choose your version of ffmpeg.
It will create a symlink in /usr/local and point to whatever version of ffmpeg you choose as the default.

You can choose your ffmpeg binary in Winff under Prefences > Linux.

---

### Post by aytuggurbuz on 2013-12-14
> **mc4man said:**
> It will use which ever binary it comes first comes across, likely will default to avconv if both are present.
As far a using FFmpeg, winff uses presets, the repo version contains ones for libavcodec53 so you may  need to import newer ones or modify the existing one or create custom ones.
They have presets for libavcodec54 here, they could work to some extent if you have an FFmpeg binary that's at libavcodec55...
[http://code.google.com/p/winff/downloads/list](http://code.google.com/p/winff/downloads/list) about halfway down

(- Don't use any Ubuntu repo supplied FFmpeg binary, pure garbage

Does that mean that if I remove avconv winff will work with ffmpeg instead? Is it safe to remove avconv or is it even possible?

Thanks for the replies!

---

### Post by mc4man on 2013-12-14
> **aytuggurbuz said:**
> Does that mean that if I remove avconv winff will work with ffmpeg instead? Is it safe to remove avconv or is it even possible?

Thanks for the replies!
As was mentioned by monkeybrain20122 you can set it in winff's preferences, see screen, in this case it's using a self built FFmpeg binary in /usr/local/bin

At some point you might mention what release of Ubuntu you're using & what FFmpeg..

---

### Post by codenine75a on 2013-12-14
use can also use your gcc compiler too.  It is called a shell application.  It is kind of easy.  You get the number of arguments and the argument array from main and basically 'Shell It Out' by using sprintf() to build your formatted console command up and use system() to execute the command.

I made this in about an hour.  Use g++ not gcc to compile it.
```

#include <stdio.h>
#include <stdlib.h>

int main(int arg, char **args)
{
int index;
char nstring[8196];
int len;
for (int index=0; index<arg; index++)
{
    printf("Converting %s to %s.mkv boss !\n",args[index],args[index]);
    len = sprintf(nstring,"ffmpeg -i %s -r 24 %s.mkv",args[index],args[index]); 

    printf("%s\n",nstring);
}
return 0;
}

```

---

### Post by codenine75a on 2013-12-15
*update Dec 15, 2013
Here is a c++ shell script code that I created to do a mass convertsion of files in the current folder where a.out resides.  Just use ./a.out * and it will pull all the files up and convert them over using ffmpeg. Compile with g++.
```

#include <stdio.h>
#include <stdlib.h>

int main(int arg, char **args)
{
int index;
char nstring[8196];
int len;
for (int index=0; index<arg; index++)
{
    printf("Converting %s to %s.mkv boss !\n",args[index],args[index]);
    len = sprintf(nstring,"ffmpeg -i \"%s\" -r 24 \"%s\".mkv",args[index],args[index]); 

    system(nstring);
}
return 0;
}


```

Cheers!

---

### Post by ssam on 2013-12-16
did you try [Arsta]("http://www.transcoder.org/") or [Transmageddon]("http://www.linuxrising.org/")?

---

### Post by FakeOutdoorsman on 2013-12-16
> **aytuggurbuz said:**
> Now I am here considering writing a Ruby GUI for ffmpeg, but I know close to nothing regarding all the codecs, formats, rates etc. I will need a full listing of all the options, and perhaps examples along with it. Then I can sit and write it. I could even distribute it to people having the same problem.
I recommend distributing a recent ffmpeg (from FFmpeg) binary with the GUI. This way you can only have to deal with one version (not to mention any forks). Otherwise you're going to be spending too much time trying to support everything. [Recent ffmpeg builds](http://ffmpeg.org/download.html#LinuxBuilds) are already available if you don't want to make it yourself.

Or you can use the FFmpeg API if you prefer (I have no experience with this but see "docs/examples" in the ffmpeg source for a start).

---

