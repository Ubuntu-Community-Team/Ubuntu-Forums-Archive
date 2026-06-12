---
title: "Mythweb Video Stream"
date: 2010-06-30
forum: Mythbuntu
---

### Post by tmcgary on 2010-06-30
I thought I had this licked but apparently not:

Is it possible to stream using VLC (or another player?) .iso files to a client computer over mythweb? 

Just to clarify NOT DVR'ed TV programming. I am referring to ripped DVDs and other content that isn't in normally accessible via the recorded programs button in MythWeb.

Currently MythWeb displays all my video content and it is available to download. Is it possible to have it streamed without downloading? Would a format change (.iso to something else) help to solve this? Even complicated workarounds are welcome.

Thanks!

Tom

---

### Post by jlagrone on 2010-07-02
I don't believe this will work with iso files, I don't have any to test it with and I suspect their would be problems if it contains more than just a single audio and video file.  If you are willing to change formats, it seems to work.  


first, modify /usr/share/mythtv/mythweb/includes/utils.php by pasting the following at the bottom.

```

/**
 * this is just copied from the video_url above and renamed as videos_url
 * some minor changes made to find video url instead of recording url
 * it allows for videos to be streamed without worrying about messing
 * up the ability to stream recordings
 *
 * @return string URL to access recordings
/**/
    function videos_url($video, $ext = false) {
    // URL override?
        if (!$ext && $_SESSION['file_url_override'])
            return 'file://'.$_SESSION['file_url_override'].str_replace('%2F', '/', rawurlencode(basename($video->filename)));
    // Which protocol should we use for downloads?

        $url = stream_url."pl/streaming/{$video->title}/{$video->subtitle}-0";
    // Handle specific file extension modes
        switch ($ext) {
        // ASX mode gets the streaming module, with a slight addition
            case 'asx' : return "$url.asx";
            case 'flvp': return "$url.flvp";
            case 'flv' : return "$url.flv";
            case 'mp4' : return "$url.mp4";
        }
    // No more dsmyth filters, so return the URL no matter what the browser is.
        return $url;
    }

```

copy the folder /var/www/mythweb/modules/stream to /var/www/mythweb/modules/streaming.  This gives a working directory that is independent from the streaming framework for the recordings so nothing accidentally gets screwed up

```
sudo cp -R /var/www/mythweb/modules/stream /var/www/mythweb/modules/streaming
```

replace the code in /var/www/mythweb/modules/streaming/tv.pl with the following.  Basically this part just finds the correct file.

```
#!/usr/bin/perl
#
# MythWeb Streaming/Download module
#
# @url       $URL: http://svn.mythtv.org/svn/trunk/mythplugins/mythweb/modules/stream/tv.pl $
# @date      $Date: 2010-05-31 21:24:33 +0100 (Mon, 31 May 2010) $
# @version   $Revision: 24924 $
# @author    $Author: kormoc $
#

    use Sys::Hostname;

# Attempt to use the perl bindings to prevent the backend from shutting down during streaming
    eval 'use MythTV;';

    if (!$@) {
        our $mythbackend = new MythTV();
        $mythbackend->backend_command('ANN Playback '.hostname);
    }

# Which show are we streaming?
    our $title    = url_param('title');
    our $subtitle = url_param('subtitle');
 
    if ($Path[1]) {
        $title    = $Path[1];
        $subtitle = $Path[2];
        $subtitle =~ s/\.\w+$//;
        $subtitle = substr $subtitle, 0, -2;
    }

# Get the basename from the database
    my $sh = $dbh->prepare('SELECT filename, length
                              FROM videometadata
                             WHERE title=? AND videometadata.subtitle = ?');
    $sh->execute($title, $subtitle);
    our ($basename, $runtime) = $sh->fetchrow_array();
    $sh->finish;

# No match?
    unless ($basename =~ /\w/) {
        print header(),
              "Unknown recording requested. $title . $subtitle . $runtime . $basename \n";
        exit;
    }

# Find the local file
    our $filename;
    $sh = $dbh->prepare('SELECT DISTINCT dirname
                           FROM storagegroup');
    $sh->execute();
    while (my ($video_dir) = $sh->fetchrow_array()) {
        next unless (-e "$video_dir/$basename");
        $filename = "$video_dir"."$basename";
    }

    $sh->finish;

    1;
```

Edit /var/www/mythweb/modules/streaming/stream_raw.pl so that it contains the appropriate containers for the video files you are using (avi, mpeg, mkv, etc. you can try adding one for iso it probably won't work but maybe you'll get lucky).  The default does not have avi or mkv for some reason so they had to be added.  This is what mine looks like.

```
#!/usr/bin/perl
#
# MythWeb Streaming/Download module
#
# @url       $URL: http://svn.mythtv.org/svn/trunk/mythplugins/mythweb/modules/stream/stream_raw.pl $
# @date      $Date: 2010-05-31 20:52:27 +0100 (Mon, 31 May 2010) $
# @version   $Revision: 24917 $
# @author    $Author: kormoc $
#

    $| = 1;

    use HTTP::Date;

# File size
    my $size = -s $filename;

# Zero bytes?
    if ($size < 1) {
        print header(),
              "$basename is an empty file.";
        exit;
    }


# File type
    my $type   = 'text/html';
    my $suffix = '';
    if ($basename =~ /\.mpe?g2?$/) {
        $type   = 'video/mpeg';
        $suffix = '.mpg';
    }
    elsif ($basename =~ /\.nuv$/) {
        $type   = 'video/nuppelvideo';
        $suffix = '.nuv';
    }
    elsif ($basename =~ /\.avi$/) {
        $type   = 'video/mpeg';
        $suffix = '.avi';
    }
    elsif ($basename =~ /\.mkv$/) {
        $type   = 'video/mpeg';
        $suffix = '.mkv';
    }
    else {
        print header(),
              "Unknown video type requested:  $basename\n";
        exit;
    }

# Download filename
    my $name = $basename;
    if ($name =~ /^\d+_\d+\.\w+$/) {
        if ($title =~ /\w/) {
            $name = $title;
            if ($subtitle =~ /\w/) {
                $name .= " - $subtitle";
            }
        }
        $name .= $suffix;
    }

# Open the file for reading
    unless (sysopen DATA, $filename, O_RDONLY) {
        print header(),
              "Can't read $basename:  $!";
        exit;
    }

# Binmode, in case someone is running this from Windows.
    binmode DATA;

    my $start      = 0;
    my $end        = $size;
    my $total_size = $size;
    my $read_size  = 1024;
    my $mtime      = (stat($filename))[9];

# Handle cache hits/misses
    if ( $ENV{'HTTP_IF_MODIFIED_SINCE'}) {
        my $check_time = str2time($ENV{'HTTP_IF_MODIFIED_SINCE'});
        if ($mtime <= $check_time) {
            print header(-Content_type           => $type,
                         -status                 => "304 Not Modified"
                        );
            exit;
        }
    }

# Requested a range?
    if ($ENV{'HTTP_RANGE'}) {
    # Figure out the size of the requested chunk
        ($start, $end) = $ENV{'HTTP_RANGE'} =~ /bytes\W+(\d*)-(\d*)\W*$/;
        if ($end < 1 || $end > $size) {
            $end = $size;
        }
        $size = $end - $start+1;
        if ($read_size > $size) {
            $read_size = $size;
        }
        print header(-status                => "206 Partial Content",
                     -type                  => $type,
                     -Content_length        => $size,
                     -Accept_Ranges         => 'bytes',
                     -Content_Range         => "bytes $start-$end/$total_size",
                     -Last_Modified         => time2str($mtime),
                     -Content_disposition => " attachment; filename=\"$name\""
                 );
    }
    else {
        print header(-type                  => $type,
                    -Content_length         => $size,
                    -Accept_Ranges          => 'bytes',
                    -Last_Modified          => time2str($mtime),
                    -Content_disposition => " attachment; filename=\"$name.$suffix\""
                 );
    }

# Seek to the requested position
    sysseek DATA, $start, 0;

# Print the content to the browser
    my $buffer;
    while (sysread DATA, $buffer, $read_size ) {
        print $buffer;
        $size -= $read_size;
        if ($size <= 0) {
            my $fileSize = -s $filename;
            my $filePos  = tell DATA;
            if ( ($fileSize - $filePos) > 0 ) {
                $size = $fileSize - $filePos;
            }
            else {
                last;
            }
        }
        if ($size < $read_size) {
            $read_size = $size;
        }
        if ($read_size < 0) {
            $read_size = 0;
        }
    }
    close DATA;

    1;
```

Finally, edit /var/www/mythweb/modules/video/tmpl/default/video.php and change (it's near the bottom).  This changes the download link to a streaming link (asx) if you want to preserve the download link, you could just put the <a href="<?php echo videos_url($video, true) ?>">  ... </a> around the image tags so that clicking the coverart would start the streaming download

```
        <div id="<?php echo $video->intid; ?>-title" class="title">
            <a href="<?php echo $video->url; ?>"><?php echo html_entities($video->title); ?></a><?php
                  if (($video->season > 0) && ($video->episode >= 0))
                      printf('(S%02d E%02d)', $video->season, $video->episode);
                  if (strlen($video->subtitle) > 0)
                      echo '<br>' . html_entities($video->subtitle);
            ?></div>
```

To

```
        <div id="<?php echo $video->intid; ?>-title" class="title">
            <a href="<?php echo videos_url($video, true) ?>"><?php echo html_entities($video->title); ?></a><?php
                  if (($video->season > 0) && ($video->episode >= 0))
                      printf('(S%02d E%02d)', $video->season, $video->episode);
                  if (strlen($video->subtitle) > 0)
                      echo '<br>' . html_entities($video->subtitle);
            ?></div>
```

---

### Post by tmcgary on 2010-07-15
jlagrone,

thanks so much for your detailed response. I was out of town for a while, so forgive my late thank you! I tried it initially with .iso and it doesnt work (I get: "...***.ISO does not exist in any  recognized storage group directories for this host" in my browser) I am going to transcode some isos and try with other formats.

A couple question for you: are you using all storage groups in your setup? Also what format did you feel was the best? Did you just use ffmpeg to (re-)encode the video content?

I initially used .iso b/c I wanted bit-for-bit copies, but I am willing to use some compression with other formats, given that iso's are problematic for many of the things I'd like to do. Thanks so much!

Tom

---

### Post by jlagrone on 2010-07-15
I'm using storage groups. Everything seemed to work fine with them, I haven't tried using it without them.  That being said all my storage groups are on the machine running the backend, mythweb, etc.  If yours are on different machines that may be a problem.  I don't use this much as I don't really have the need to stream on a regular basis.

I do remember seeing that error message when I was putting this together.  Does it have the correct filename for whatever you were trying to play?  

I have been using handbrake and encoding the movies in h264 in mkv containers using the high quality profile with a few adjustments (quality 18 and uneven multihexagon for motion estimation).  It takes forever on my system, averaging about 2.5 times the play length so typically 4-6 hours, but I can't tell the difference quality wise.  Files are about a 1/4 of the raw size.  And you can throw in as many audio tracks and subtitles as you want (probably won't be able to change off the default while streaming though).  I don't know if that is the best, I'm not all that familiar with the various options available this is just easy for me to deal with as there is a gui and I don't end up really confused trying to figure out what options to use.

You might also take a look at UPnP streaming ([http://www.mythtv.org/wiki/UPnP](http://www.mythtv.org/wiki/UPnP)).  It does not work with ISO and I'm not sure how compatible it is with storage groups at this point.

---

### Post by tmcgary on 2010-07-16
When I got the error message trying to use .ISO it referenced the correct file, it just couldnt play it back. 

I converted a file to .AVI using k9copy and corrected my storage groups and local videos. They showed up correctly in mythweb, but when I click the title for playback VLC opens and requests a login. However after logging in, VLC just sits there with no time displayed and no video :(.

I think I will try a different container/format to see if that helps.

Thanks for the link for UPnP. My ultimate goal is to be able to to stream my video and music to a smart phone. I have 9 months till my contract is up to try to get this to work :). Did you have any experience with this?

---

### Post by jlagrone on 2010-07-16
I have just started toying with the UPnP.  I have been using it to stream videos to my xbox.  It seems to work with basically no setup whatsoever for me but some of my videos don't show up.  I think this is just the xbox not liking mkv files or something along those lines but I haven't gotten around to actually learning about it yet.  It was mostly just one of those, I wonder if this will work moments when I happened to see it.  If it's an option, this will probably be a better solution for you assuming the smartphone in question has some sort of UPnP client (there's almost certainly an app if it's not built in)

As for the mythweb stuff, try saving the asx file.  Open it with a text editor and there should be a url for the video in it.  Try pasting that directly in the browser - it should ask you to download the file or give you an error message similar to what you saw with the iso.  Also do the recordings stream fine?  This is really just the recordings streamer slightly re-purposed, so if those don't work I wouldn't expect this to.  You might just need to modify htaccess, htdigest, or whatever you are using to secure mythweb to include mythweb/modules/streaming.

---

### Post by tmcgary on 2010-07-16
I think you are right with the UPnP being an easier solution for a smartphone (the HTC Evo 4G looks awesome for this). I believe this app might do what I want: [http://andromote.de/](http://andromote.de/) Its a bit ambiguous as to whether it will work outside of an internal home network, but I'm hopeful.

I tried the cut and paste method after downloading the .asx file and retrieving the URL from the file text. It gave me a similar message to the ISO, "Unknown video type requested:  2001 A Space Odyssey.m4v". I believe this is because I didn't define how to handle that file extension as you indicated in your initial post.

I will fix that and see if it works and verify that DVR recordings are functional as well. Thanks again for all your help!

tom

---

### Post by jlagrone on 2010-07-16
I think accessing UPnP from an external network may be problematic.  Not necessarily connecting and streaming, that should be simple enough it's just a matter of figuring out how to point the recieving device to the server.  However, in my cursory searches it does not appear that there is an easy way to secure it to prevent the outside world from being able to access it.  Also I suspect any competitent network administrator would disable the UPnP features on their networks because it potentially brings security risks making it difficult to connect.

For the m4v, I believe this is what you'll want to add in.

```

elsif ($basename =~ /\.m4v$/) {
        $type   = 'video/x-m4v';
        $suffix = '.m4v';
    }

```

Some players seem to be really picky about it being correct (just google for "*** mime type" where *** is your extention).  Others like vlc don't seem to care, mythweb seems happy enough to stream it as long as you put something there.  I think I just put mpeg for everything and that seemed to work.

I'm currently in the process of moving, but when I get more free time I'll try to to clean all of this up and submit it as a feature request upstream.  It's possible, albeit unlikely, that video streaming could be in an official release in your time frame.  In the meantime, I'll try to keep pointing you in the right direction.

---

### Post by tmcgary on 2010-07-16
Re UPnP security risks, I agree. After doing about 30 minutes of reading online it seems like it is a large security risk and that somehow authenticating outside clients would be very difficult. Makes me wonder about my xbox 360 needing the UPnP open on my router...

I fudged the m4v entry in stream_raw.pl as mpeg, and just as you said VLC didnt care. I will correct that to avoid future problems. After fixing the m4v entry, I was able to stream my video content. The biggest problem was buffering. My router is a linksys WRT54g workhorse and the client was using wireless N, so the latter could be the problem. It may be time to upgrade to a gigabit-wireless N router too.

I suppose I need to increase the buffer in VLC as well. I may recode all the video into a more compressed format specifically for mobile use. Again thanks for your help, this is awesome! I would love to see this implemented in future releases. 

tom

---

### Post by tmcgary on 2010-07-23
jlagrone,

As my problems have changed from just getting the video to work to more of a network/buffering issue I started a new thread. 
[http://ubuntuforums.org/showthread.php?p=9626837#post9626837](http://ubuntuforums.org/showthread.php?p=9626837#post9626837)

I apologize if this is inconvenient; I realize now its a little annoying. I hope your move went smoothly. My wife and I have moved 5 times in 8 years of marriage-it always sucks!!

tom

---

### Post by Astray on 2010-08-15
Hi there,

Great job such a 'tutorial'... but the url created (to become a asx download) isn't correct i think.. on my server it is:
[http://localhost//mythweb/pl/streaming/Weird%20Science%20XviD%20DVDRip-iNfInItE%20424/-0.asx](http://localhost//mythweb/pl/streaming/Weird%20Science%20XviD%20DVDRip-iNfInItE%20424/-0.asx)

I think the "/-0" at the end isn't necessary ... but when i change it in the file utils.php to create a url like:
[http://localhost//mythweb/pl/streaming/Weird%20Science%20XviD%20DVDRip-iNfInItE%20424.asx](http://localhost//mythweb/pl/streaming/Weird%20Science%20XviD%20DVDRip-iNfInItE%20424.asx)

The following message apears on the client computer when i click it:
Unknown recording requested. Weird Science XviD DVDRip-iNfInItE 424 .  .  .   

Well... any suggestions? 

Hope that i can stream to the internet so i can see movies on my holliday address! ;-)

Greetz,
Astray

---

### Post by jlagrone on 2010-08-15
If you took out the "/-0" part in util.php, you'll also need to take out the references to subtitle in tv.pl. The "/-0" part is a place holder so that subtitles can be used - this is primarily for TV shows because it won't find a unique file with a title alone.  If there is no subtitle, which is generally the case with movies, it produces a url with .../somemovie/.asx, which doesn't work as it is scripted without a place holder (I'm sure it could with a few modifications, but this was all hacked together using as much of the original scripts as possible -- so attributed it to laziness and a poor knowledge of perl scripts)

I'm in the process of cleaning this up so I can submit it upstream as a feature request.  I hope to finish it up within the next week or so, but that's dependent on how much free time is available and such.

---

### Post by Astray on 2010-08-24
I used the 'guide' above to stream the movies on my server.. but the url is not oke ie:
[http://localhost//mythweb/pl/streaming/Weird%20Science%20XviD%20DVDRip-iNfInItE%20424/-0.asx](http://localhost//mythweb/pl/streaming/Weird%20Science%20XviD%20DVDRip-iNfInItE%20424/-0.asx) 

I changed is to [http://loccalhost//mythweb/pl/streaming/Weird%20Science%20XviD%20DVDRip-iNfInItE%20424.asx](http://loccalhost//mythweb/pl/streaming/Weird%20Science%20XviD%20DVDRip-iNfInItE%20424.asx)

But still no working stream..

Anybody a suggestion?

BTW the firefox screen says:
Unknown recording requested. Weird Science XviD DVDRip-iNfInItE 424 .  .  .   

Cheers..

Astray

---

### Post by tmcgary on 2010-08-24
Astray,

you may have done this already, but just wanted to check:

Did you add a MIME type line for XVID?

Second thought, that might be coverted under the mpeg type

---

