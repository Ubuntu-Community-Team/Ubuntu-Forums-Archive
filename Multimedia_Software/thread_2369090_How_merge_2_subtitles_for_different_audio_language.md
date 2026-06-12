---
title: "How merge 2 subtitles for different audio languages"
date: 2017-08-18
forum: Multimedia Software
---

### Post by rmstock2 on 2017-08-18
[COLOR=#000000]Create Joined and Sorted .srt Subtitles :[/COLOR]

I created a straightforward solution for myself, which works. First both .srt files
[COLOR=#000000]Movie-english-parts.srt and [/COLOR][COLOR=#000000]Movie-spanish-parts.srt [/COLOR][COLOR=#000000]
[/COLOR]need of be synced properly with the video. For that use gnome-subtitles.
Next i wrote a util written in c to read the combined .srt file :

```

#include <stdio.h>
#include <stdlib.h>

#define MAXLINE    1000    /* maximum input line size */

int getline_srt(char line[], int maxline);

/* Read a SubRip (*.srt) file, to make it ready for Time sorting :
   Usage : ./readsrt < inputfile.srt > sortfile
*/
int main()
{
    int  i; 
    int  len;        /* line length */
    char line[MAXLINE];    /* current line */

    while ((len = getline_srt(line, MAXLINE)) > 0) {
        for (i = 0; i<len-1 ; ++i) 
            printf("%c",line[i]);
        if (len > 1) 
            printf("###");
        else
            printf("===\n");
    }
    exit(0);
}

/* getline_srt: read a line line into s, return length */
int getline_srt(char s[], int lim)
{
    int c, i;

    for (i=0; i<lim-1 && (c=getchar())!=EOF && c!='\n'; ++i)
        s[i]=c;
    if (c == '\n') {
        s[i]=c;
        ++i;
    }
    s[i] = '\0';
    return i;
}
```

Save the code as readsrt.c and  compile it with `[COLOR=#000000]make readsrt' or
[/COLOR][COLOR=#000000]cc     readsrt.c   -o readsrt . Next do the following

[/COLOR]```
[COLOR=#000000]$ cat Movie-english-parts.srt Movie-spanish-parts.srt > joined.srt
[/COLOR][COLOR=#000000]$ readsrt < joined.srt > foo
[/COLOR][COLOR=#000000]$ cat foo | sed 's/^...###//' | sed 's/^..###//' | sed 's/^.###//' > foo2
[/COLOR][COLOR=#000000]$ sort -n foo2 > foo3
[/COLOR][COLOR=#000000]$ cat foo3 | awk '{printf "%d###%s\n", NR, $0}' > foo4
[/COLOR][COLOR=#000000]$ cat foo4 | sed 's/###/\n/g' | sed 's/===//' > sorted.srt[/COLOR]
```[COLOR=#000000]
[/COLOR][COLOR=#000000]
[/COLOR]Try to read sorted.srt with gnome-subtitles, which is 
the defacto gui subtitles standard package .

---

### Post by TheFu on 2017-08-18
My video editing software knows how to handle embedded captions correctly, at least for mpeg2 videos.  It deals with SRT, captions, and SUBS.

For all other types, I put the videos (vid/audio/captions) into a single mkv container (**mkvmerge**) with the desired order.  It handles any SRT renumbering required and timing fixes due to the merge.  For splitting videos, I also use **mkvmerge --split parts:  **  

Once or twice, I've needed to use gnome-subtitles. Always found it to be a pain.  There is a perl script that handles pretty much anything related to SRT processing.  If I need to change frame rates, there is also the Subtitles CPAN module.  The only trick is to use whole numbers in the math when calculating frame rates: 30000/1001, 25000/1001, 24000/1001  for example.

mkv containers easily support 10-100 different subtitles/caption tracks.  Here's a TV recording from a telenovela last night:
| + Duration: 2489.780s (00:41:29.780)
|  + Codec ID: V_MPEG4/ISO/AVC
|  + CodecPrivate, length 41 (h.264 profile: Main @L4.0)
|  + Codec ID: A_AC3
|   + Channels: 2
|  + Codec ID: A_VORBIS
|   + Channels: 2
|  + CodecPrivate, length 4367
|  + Codec ID: S_TEXT/ASS
|  + CodecPrivate, length 480
|  + Codec ID: S_TEXT/ASS
|  + CodecPrivate, length 486

English and Spanish SRTs were part of the broadcast in cc1 and cc3.  I used ccextractor to pull the SRT tracks out after removing any commercials.  That make cc1.srt and cc3.srt files, which I muxed back into the mkv during the transcode from mpeg2 --> h.264 with handbrake.  I kept the original audio, but also generated vorbis audio, since some of my playback devices don't support DTS], but they all support multichannel vorbis.

Text processing using C is painful.  You really should initialize all variables to known values in the C code, BTW. Also, perl would be faster both at runtime and in the coding.

---

