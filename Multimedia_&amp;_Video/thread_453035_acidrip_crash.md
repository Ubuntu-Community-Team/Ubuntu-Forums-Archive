---
title: "acidrip crash"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by nimajiman on 2007-05-23
Hi there,
Im a bit of a newb with Ubuntu. so bear with me. I'm running feisty and trying to use acidrip. All was working fine this morning, have ripped a couple of DVDs no problem, until I updated a few things and now acidrip just crashes when i click on the 'load DVD' button.

I have libdvdcss2 installed, and can watch DVDs fine through VLC and Mplayer. From memory, I did a few updates this morning like added totem-xine and removed totem-gstreamer, (as i get the impression that xine is more reliable?) and added some other things through apt-get (ubuntu-restricted-extras, libxine-extracodecs, gstreamer0.8-plugins, gstreamer0.8-plugins-multiverse, gstreamer0.8-ffmpeg) largely in an effort to get amarok playing mp3s properly (which it now does). 

Since then acidrip wont get past loading a DVD, so I retreated and went back to totem-gstreamer instead of xine, but the problem is still there.

Anyone got any ideas? It sounds like a similar problem to the one posted here [http://ubuntuforums.org/showthread.php?t=427748&highlight=acidrip](http://ubuntuforums.org/showthread.php?t=427748&highlight=acidrip) but thought I would start a new thread as that one seems to have died off.

Cheers

---

### Post by benanzo on 2007-05-24
Try starting acidrip from a terminal so you can watch the output when it crashes.

```
acidrip
```

Just a guess, but if it is dying when you select to load the DVD, there might be a problem with libdvdread.  Either make sure it is installed, or possibly reinstall it.  Are your other applications (MPlayer) still able to load and play DVDs?  acidrip uses MPlayer/Mencoder as it's backends, so if there is a problem, that's where you would look.

---

### Post by nimajiman on 2007-05-24
Thanks for the help, much appreciated.

I tried a few things based on what you wrote. Here they are:

(1) First I typed 
```
sudo apt-get install libdvdread3
```
 just to check that it was installed. It said libdvdread3 is already newest version, then the next line said > libdvdread3 set to manual installed. 
Not sure what that means exactly but I don't remember seeing that line before with any other package installed from command line. I then typed 
```
sudo apt-get remove libdvdread3
```
to try a reinstall, but mr command line said he was going to remove a bunch of other things as well such as vlc, mplayer, acidrip, firefox plugins etc, so I decided to cancel.

(2) I started acidrip from command line. Loaded fine, then when I clicked on 'load DVD' it crashed as before. This is what i got on the command line: 
> Pango-WARNING **: shape engine failure, expect ugly output. the offending font is 'DejaVu Sans Not-Rotated 0' at /usr/bin/acidrip line 60.
Segmentation fault (core dumped)
I'm guessing this is where my problem is, but i have no idea what any of this means!

(3) Lastly I thought i'd check my mplayer just to make sure it does play DVD's. Well, I thought it did, but when I went 'open disc' it said 
> Fatal Error: Error opening/initialising the selected video_out (-vo) device. Not sure if this problem is related to the problem with acidrip, but my guess is that it would be. I'm pretty sure mplayer played my DVD's before today. 
I tried VLC also but it is still able to play DVD's.

Sorry this became such a long post! Any further ideas?

---

### Post by nimajiman on 2007-05-24
*Addendum*

Thought i'd post the contents of /usr/bin/acidrip, as this seems to be where the problem is.

> #!/usr/bin/perl -w

eval 'exec /usr/bin/perl -w -S $0 ${1+"$@"}'
    if 0; # not running under some shell

require 5.005;
use strict;
use vars qw($VERSION);

$VERSION = '0.14';

package acidrip;

use AcidRip::acidrip;
use Getopt::Long;

sub version {
  print "AcidRip - Version $::VERSION \"Written\" by Chris Phillips <acid_kewpie\@users.sourceforge.net>\n";
  exit 0;
}

@ARGV = ( '-x', @ARGV ) if ( scalar @ARGV );

my %opts = ();
GetOptions(
  'x|no-gui'     => \$opts{'x'},
  'c|crop=i'     => \$opts{'c'},
  't|track=i'    => \$opts{'t'},
  'v|version'    => \$opts{'v'},
  'f|filename=s' => \$opts{'f'},
  'h|help'       => \$opts{'h'}
);

$::settings = new acidrip_settings;
$::playlist = new acidrip_playlist;

$::settings->load_settings;

$::messages = new acidrip_messages($::settings->{'ui_language'});
$::dvd      = ();

version() if $opts{'v'};

$::widgets = new acidrip;

$::settings->{'verbose'} = 0;
load_settings_to_interface();    
$::settings->{'verbose'} = 1;

get_available_codecs();    

$::widgets->{'acidrip'}->show;

if ( $::settings->{'autoload'} ) {
  $::widgets->{'read_dvd_button'}->clicked;
  $::widgets->{'crop_detect_button'}->clicked if $::settings->{'crop_enable'};
}
message("AcidRip $::VERSION, \"Written\" by C.Phillips <acid_kewpie\@users.sf.net>");

main Gtk2;

exit 0;

__END__

Line 60 is the one that says "main Gtk2;", just near the end.

---

### Post by Milos_SD on 2007-06-06
You can fix this by downgrading this three packages to feisty's default: libfreetype6,  libcairo2, libxft2

This packages were upgraded with "How to improve sub-pixel font rendering for Feisty" section in Feisty starter guide. :)

Sorry for my english.

---

### Post by nimajiman on 2007-06-18
Ok, i'll give it a try, though not sure how to best go about doing a downgrade. If i go into synaptic and find the packages and choose 'force version' will that work?

---

### Post by nimajiman on 2007-06-19
Awesome! Thanks heaps for the info - i forced the packages you mentioned to their previous versions, and acidrip worked fine! I didnt really notice much difference with the improved sub-pixel font rendering anyway, so I happy to live without if it means acidrip works again.

Thanks again

---

### Post by Milos_SD on 2007-06-29
You are welcome. :)

---

