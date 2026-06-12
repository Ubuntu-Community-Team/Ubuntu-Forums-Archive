---
title: "problem: special characters in .m3u playlists"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by antigoon on 2007-11-10
Summary:
I've got mp3s with foreign characters in the names (stupid, I know) and when I try to read existing playlists with those songs, it doesn't work. 

Details:

I bought a new computer and am trying to move everything I do over to Ubuntu from Windows. So far so good. Except for music playing.

I can easily import my mp3 files into a music player, but I'm having trouble importing my playlists. I've got mp3s with foreign characters in the names (stupid, I know) and although the .mp3 files themselve are perfectly recognized by the music players, playlists referencing those songs do not import properly. (The rest of the songs in the playlist get seen, just not the ones with special characters.)

Playlists are especially important because they're also the easiest way to copy star ratings from one program to another (create playlists named 1.m3u, 2.m3u, ... 5.m3u in the source program and then import them and change the star values in the destination program.)

In Windows, I used Mediamonkey to organize my music and had it rename all my music ot be something like "/<genre>/<Artist>-<Album>-<track>-<track title>.mp3.

But for albums like "Saint Germain des Prés Café", or even "I'm a Mountain" (notice the embedded apostrophe), I can't get Rhythmbox or Armorak to import them properly. Banshee just hangs.

I could go through a massive file renaming exercise, but it would involve renaming both the files and the corresponding entries in the playlists, a surefire error-prone operation.

Any ideas? Anything I can change with character encoding, unicode, or something? Any outsite-the-box crazy ideas to try?

Thanks,
Stephen

---

### Post by citybird on 2007-11-10
same problem here. anyone know the answer?

---

### Post by antigoon on 2007-11-10
I think I've found an answer to my own question. The problem is in character-encoding. My m3u playlists were encoded in Windows latin 1 (aka cp-1259 aka windows-1259 aka ISO-8859-1 plus some other stuff) and I guess most linux apps are expecting utf8 encoding.

I searched around and couldn't find a canned script to do it for me, but I found enough info that I could write my own little perl script to do it for me.

```
#!/usr/bin/perl
[COLOR="Blue"]#
#  windowsToLatin.pl. Run windowsToLatin.pl {input file} > {output file}
#
# If perl complains that it doesn't know about Unicode::String, you must install the module.
#   $ > perl -MCPAN -e 'shell'
#   cpan>   <set up initial environment. just hit return to accept the defaults>
#   cpan> install Unicode::String
#[/COLOR]
use Unicode::String;

Unicode::String->stringify_as( 'utf8' ); # utf8 already is the default

open(INFILE,"<$ARGV[0]") || die("cannot open input file $ARGV[0]\n");
while (<INFILE>)
  {
    my $string_utf8 = Unicode::String::latin1($_);
    #$string_utf8 =~ s#\\#/#g; [COLOR="Blue"]#uncomment this line if you want to replace dos/windows backslashes '\'
                               #with unix forward slashes '/'[/COLOR]
    print $string_utf8;
  }
close INFILE;

```

I feel foolish having posted to the forum and then being able to come up with the answer myself so quickly, but I really was at my witt's end and it really was while doing something completely different that I came across the solution.

Steve

---

