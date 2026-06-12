---
title: "HOWTO: Songbird and wma files"
date: 2007-03-14
forum: Multimedia &amp; Video
---

### Post by GreenDevil on 2007-03-14
Hello everyone, GreenDevil here with my first official post. Been a community member for a couple of months now, but I've never really had a reason to post until now :)

I bring with me today a howto on Songbird and those pesky wma files, for those of us who are too lazy to convert them to something not evil, or have other reasons for needing the wma files.

After hours of scanning these and other forums searching for a way to make it work, I have pieced together a howto that works for me.

First, open up a terminal and go to the Songbird chrome directory:
> cd /opt/Songbird/chrome

Next, we need to edit a file from the songbird.jar file, so we will need to open that up like so:
> sudo file-roller songbird.jar

Now, open the content folder, followed by the songbird then scripts folder, find the file called coreGStreamerSimple.js and drag that to your desktop, leave archive manager open as we are going to add to it in a moment.

Open it up in your favorite editor, now we are going to add wma support to the "mediaUrlExtensions" section. It should look like this:
> this._mediaUrlExtensions = ["mp3", "ogg", "flac", "mpc", "wav", "m4a", "m4v",
                              "wmv", "asf", "avi",  "mov", "mpg", "mp4", "ogm",
                              "mp2", "mka", "mkv", "wma"];

Save the file, and drag that back over to the archive manager/songbird.jar file. close it, then fire up songbird and add your favorite wma files!

- GreenDevil

---

### Post by dberg on 2007-03-14
I am unable to find the file or the directory that you mention.

There is no Songbird directory in my /opt

I have also used Beagle to search for songbird.jar and coreGStreamerSimple.js but find nothing.

Do you have any suggestions of where or how I might find that file?

Thanks

---

### Post by GreenDevil on 2007-03-14
How did you install Songbird? Via automatix or via their website?

I did the first install via automatix, then updated it recently via their website downloads, but if you follow the install instructions to a T it puts it in the /opt directory.

Where is songbird installed on your system?

- GreenDevil

---

### Post by dberg on 2007-03-14
I think I had done it using a thread on here... not sure though.

Anyways, I finally found it!

It was in /usr/local/bin/songbird/chrome

So I edited the file as you said, now I get this error when opening Songbird.

> SBAppInitialize
ReferenceError: CoreGStreamerSimpleDocumentInit is not defined

any suggestions?

---

### Post by GreenDevil on 2007-03-14
I will post my whole coreGStreamerSImple.js file for you:

Try copying all of this. Make sure Songbird is not running. You may have not put the quotes around wma, ex "wma", which is causing the script to error out like that.

> /*
//
// BEGIN SONGBIRD GPL
//
// This file is part of the Songbird web player.
//
// Copyright(c) 2005-2007 POTI, Inc.
// [http://songbirdnest.com](http://songbirdnest.com)
//
// This file may be licensed under the terms of of the
// GNU General Public License Version 2 (the "GPL").
//
// Software distributed under the License is distributed
// on an "AS IS" basis, WITHOUT WARRANTY OF ANY KIND, either
// express or implied. See the GPL for the specific language
// governing rights and limitations.
//
// You should have received a copy of the GPL along with this
// program. If not, go to [http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html)
// or write to the Free Software Foundation, Inc.,
// 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.
//
// END SONGBIRD GPL
//
 */

/**
 * \file coreGStreamerSimple.js
 * \brief The CoreWrapper implementation for the GStreamer simple component
 * \sa sbICoreWrapper.idl coreBase.js
 */

/**
 * \class CoreGStreamerSimple
 * \brief The CoreWrapper for the simple GStreamer Simple component
 * \sa CoreBase
 */
function CoreGStreamerSimple()
{
  this._object = null;
  this._url = "";
  this._id = "";
  this._paused  = false;
  this._oldVolume = 0;
  this._muted = false;

  this._mediaUrlExtensions = ["mp3", "ogg", "flac", "mpc", "wav", "m4a", "m4v",
                              "wmv", "asf", "avi",  "mov", "mpg", "mp4", "ogm",
                              "mp2", "mka", "mkv", "wma", "wmv"];
  this._mediaUrlSchemes = ["mms", "rstp"];

  this._videoUrlExtensions = ["wmv", "asf", "avi", "mov", "mpg", "m4v", "mp4",
                              "mp2", "mpeg", "mkv", "ogm"];

  this._unsupportedExtensions = [];

  this._mediaUrlMatcher = new ExtensionSchemeMatcher(this._mediaUrlExtensions,
                                                     this._mediaUrlSchemes);
  this._videoUrlMatcher = new ExtensionSchemeMatcher(this._videoUrlExtensions,
                                                     []);

  this._uriChecker = null;
};

// inherit the prototype from CoreBase
CoreGStreamerSimple.prototype = new CoreBase();

// set the constructor so we use ours and not the one for CoreBase
CoreGStreamerSimple.prototype.constructor = CoreGStreamerSimple();

CoreGStreamerSimple.prototype.playURL = function ( aURL )
{
  this._verifyObject();

  if (!aURL) {
    throw Components.results.NS_ERROR_INVALID_ARG;
  }

  aURL = this.sanitizeURL(aURL);
  this._paused = false;

  try
  {
    if(this._object.isPlaying || this._object.isPaused)
    {
      this._object.stop();
    }

    // In 0.2.5, the video window always unfullscreens between videos
    // because staying fullscreen currently creates too many problems
    // this will change in 0.3

    if (isMaximized())
      restoreWindow();

    this._object.fullscreen = false;

    var ioService =
      Components.classes["@mozilla.org/network/io-service;1"]
                .getService(Components.interfaces.nsIIOService);

    var uri = ioService.newURI(aURL, null, null);

    // If this is a local file, just play it
    if (uri instanceof Components.interfaces.nsIFileURL) {
      this._object.uri = aURL;
      this._object.play();
      return true;
    }
    else {
      // Resolve the network URL
      return this._resolveRedirectsAndPlay(uri);
    }

  }
  catch(e)
  {
      this.LOG(e);
  }

  return true;
};

CoreGStreamerSimple.prototype._resolveRedirectsAndPlay = function(aURI) {

  // Cancel any old checkers
  if (this._uriChecker) {
    this._uriChecker = null;
  }

  // Make a new uriChecker and initialize it
  var uriChecker =
    Components.classes["@mozilla.org/network/urichecker;1"]
              .createInstance(Components.interfaces.nsIURIChecker);
  uriChecker.init(aURI);

  // Save it away so we can cancel if necessary. Can't do this until after the
  // init call.
  this._uriChecker = uriChecker;

  // And begin the check
  uriChecker.asyncCheck(this, null);

  return true;
};

CoreGStreamerSimple.prototype.play = function ()
{
  this._verifyObject();

  this._paused = false;

  try
  {
    this._object.play();
  }
  catch(e)
  {
    this.LOG(e);
  }

  return true;
};

CoreGStreamerSimple.prototype.pause = function ()
{
  if( this._paused )
    return this._paused;

  this._verifyObject();

  try
  {
    this._object.pause();
  }
  catch(e)
  {
    this.LOG(e);
  }

  this._paused = true;

  return this._paused;
};

CoreGStreamerSimple.prototype.stop = function ()
{
  this._verifyObject();

  try
  {
    this._object.stop();
    this._paused = false;
  }
  catch(e)
  {
    this.LOG(e);
  }

  return true;
};

CoreGStreamerSimple.prototype.getPlaying = function ()
{
  this._verifyObject();
  var playing = (this._object.isPlaying || this._paused) && (!this._object.isAtEndOfStream);
  return playing;
};

CoreGStreamerSimple.prototype.getPlayingVideo = function ()
{
  this._verifyObject();
  return this._object.isPlayingVideo;
};

CoreGStreamerSimple.prototype.getPaused = function ()
{
  this._verifyObject();
  return this._paused;
};

CoreGStreamerSimple.prototype.getLength = function ()
{
  this._verifyObject();
  var playLength = 0;

  try
  {
    if(this._object.lastErrorCode > 0) {
      return -1;
    }
    else if(!this.getPlaying()) {
      playLength = 0;
    }
    else {
      playLength = this._object.streamLength / (1000 * 1000);
    }
  }
  catch(e)
  {
    if(e.result == Components.results.NS_ERROR_NOT_AVAILABLE)
    {
      return -1;
    }
    else
    {
      this.LOG(e);
    }
  }

  return playLength;
};

CoreGStreamerSimple.prototype.getPosition = function ()
{
  this._verifyObject();
  var curPos = 0;

  try
  {
    if(this._object.lastErrorCode > 0) {
      return -1;
    }
    else if(this._object.isAtEndOfStream || !this.getPlaying()) {
      curPos = 0;
    }
    else {
      curPos = Math.round(this._object.position / (1000 * 1000));
    }
  }
  catch(e)
  {
    if(e.result == Components.results.NS_ERROR_NOT_AVAILABLE)
    {
      return -1;
    }
    else
    {
      this.LOG(e);
    }
  }

  return curPos;
};

CoreGStreamerSimple.prototype.setPosition = function ( pos )
{
  this._verifyObject();

  try
  {
    this._object.seek( pos * (1000 * 1000) );
  }
  catch(e)
  {
    this.LOG(e);
  }
};

CoreGStreamerSimple.prototype.getVolume = function ()
{
  this._verifyObject();
  return Math.round(this._object.volume * 255);
};

CoreGStreamerSimple.prototype.setVolume = function ( volume )
{
  this._verifyObject();

  if ((volume < 0) || (volume > 255))
    throw Components.results.NS_ERROR_INVALID_ARG;

  this._object.volume = volume / 255;
};

CoreGStreamerSimple.prototype.getMute = function ()
{
  this._verifyObject();
  return this._muted;
};

CoreGStreamerSimple.prototype.setMute = function ( mute )
{
  this._verifyObject();

  if(mute)
  {
    this._oldVolume = this.getVolume();
    this._muted = true;
  }
  else
  {
    this.setVolume(this._oldVolume);
    this._muted = false;
  }
};

CoreGStreamerSimple.prototype.getMetadata = function ( key )
{
  this._verifyObject();
  var rv;

  switch(key) {
      case "title":
        rv = this._object.title;
      break;
      case "album":
        rv = this._object.album;
      break;
      case "artist":
        rv = this._object.artist;
      break;
      case "genre":
        rv = this._object.genre;
      break;
      case "url": {
      // Special case for URL... Need to make sure we hand back a complete URI.
       var ioService =
          Components.classes[IOSERVICE_CONTRACTID].getService(nsIIOService);
        var uri;
        try {
          // See if it is a file, first.
          var file =
            Components.classes["@mozilla.org/file/local;1"]
                      .createInstance(Components.interfaces.nsILocalFile);
          file.initWithPath(this._object.uri);
          var fileHandler =
            ioService.getProtocolHandler("file")
                     .QueryInterface(Components.interfaces.nsIFileProtocolHandler);
          var url = fileHandler.getURLSpecFromFile(file);
          uri = ioService.newURI(url, null, null);
        }
        catch (err) { }
        
        if (!uri) {
          try {
            // See if it is a regular URI
            uri = ioService.newURI(this._object.uri, null, null);
          }
          catch (err) { };
        }
        
        if (uri)
          rv = uri.spec;
      }
      break;
      default:
        rv = "";
      break;
  }

  return rv;
};

CoreGStreamerSimple.prototype.goFullscreen = function ()
{
  this._verifyObject();
  var fs = isMaximized();
  if (fs) restoreWindow(); else maximizeWindow();
  this._object.fullscreen = !fs; 
};

  
CoreGStreamerSimple.prototype.isMediaURL = function ( aURL )
{
  return this._mediaUrlMatcher.match(aURL);
}

CoreGStreamerSimple.prototype.isVideoURL = function ( aURL )
{
  return this._videoUrlMatcher.match(aURL);
}

CoreGStreamerSimple.prototype.getSupportedFileExtensions = function ()
{
  return new StringArrayEnumerator(this._mediaUrlExtensions);
}

CoreGStreamerSimple.prototype.getSupportForFileExtension = function(aFileExtension)
{
  // Strip the beginning '.' if it exists and make it lowercase
  var extension =
    aFileExtension.charAt(0) == "." ? aFileExtension.slice(1) : aFileExtension;
  extension = extension.toLowerCase();

  // TODO: do something smarter here
  if (this._mediaUrlExtensions.indexOf(extension) > -1)
    return 1;
  else if (this._unsupportedExtensions.indexOf(extension) > -1)
    return -1;

  return 0; // We are the default handler for whomever.
};

CoreGStreamerSimple.prototype.onStartRequest = function(request, context)
{
  // Nothing to do here.
};

CoreGStreamerSimple.prototype.onStopRequest = function(request, context, status)
{
  if (request != this._uriChecker) {
    return;
  }

  if (status == NS_BINDING_SUCCEEDED) {
    // Clear immediately so we can't try to cancel it anymore
    this._uriChecker = null;

    var uriChecker =
      request.QueryInterface(Components.interfaces.nsIURIChecker);
    var url = uriChecker.baseChannel.URI.spec;

    this._url = url;
    this._object.uri = url;
    this._object.play();
  }
};

/**
  * See nsISupports.idl
  */
CoreGStreamerSimple.prototype.QueryInterface = function(iid) {
  if (!iid.equals(Components.interfaces.sbICoreWrapper) &&
      !iid.equals(nsIRequestObserver) &&
      !iid.equals(Components.interfaces.nsISupports))
    throw Components.results.NS_ERROR_NO_INTERFACE;
  return this;
};

/**
 * ----------------------------------------------------------------------------
 * Global variables and autoinitialization.
 * ----------------------------------------------------------------------------
 */
try {
  var gGStreamerSimpleCore = new CoreGStreamerSimple();
}
catch(err) {
  dump("ERROR!!! coreGStreamerSimple failed to create properly.");
}

/**
  * This is the function called from a document onload handler to bind everything as playback.
  */
function CoreGStreamerSimpleDocumentInit( id )
{
  try
  {
    var gPPS = Components.classes["@songbirdnest.com/Songbird/PlaylistPlayback;1"]
                         .getService(Components.interfaces.sbIPlaylistPlayback);
    var videoElement = document.getElementById( id );
    gGStreamerSimpleCore.setId("GStreamerSimple1");
    var gstSimple = Components.classes["@songbirdnest.com/Songbird/Playback/GStreamer/Simple;1"]
                              .createInstance(Components.interfaces.sbIGStreamerSimple);
    gstSimple.init(videoElement);
    gGStreamerSimpleCore.setObject(gstSimple);
    gPPS.addCore(gGStreamerSimpleCore, true);
  }
  catch ( err )
  {
    dump( "\n!!! coreGStreamerSimple failed to bind properly\n" + err );
  }
};


---

### Post by GreenDevil on 2007-03-14
Went back and checked my howto, I accidentally added a comma to the end of the line, by bad. . .  It's fixed now :)

- GreenDevil

---

### Post by dberg on 2007-03-14
is there a reason your file has "wmv" twice?

---

### Post by dberg on 2007-03-14
I replaced your file with mine but still get the error. I must have something somewhere else messed up as well. I think I might just try a fresh install.

---

### Post by GreenDevil on 2007-03-14
Yeah I had some oddball audio files as wmv for some reason, and added that in there to see if I could get them to play.

Not sure why it's not working for you, I just did the same thing on a friend's pc and it worked fine, I'm anxious to see other people try it now, any input is welcome.

- GreenDevil

---

### Post by Sean K on 2007-03-25
I tried this, but it didn't work. There was no error, it just didn't work. Songbird let me add the WMA files to my library, but when I tried to play them, nothing happened. It just "Error" up top, where it normally says the length of the song when you're playing it. Any ideas? Amarok plays them, but skips a bit.

---

### Post by aditya.rachakonda on 2007-04-29
Works like a charm GreenDevil, Thanks.

---

### Post by keryil on 2007-05-19
It worked flawlessly. I could play wma's on totem or gstream via the command line but this extension thing was driving me crazy. Nice work, appreciated.

---

### Post by kevindubrow on 2007-08-28
Hey, I just got the latest Songbird file off the website (Songbird_0_2_5_linux-i686.tar.gz). How exactly do I install it? Thanks.

---

### Post by cndymncntrbnd on 2008-02-20
Well, I searched around for the coreGStreamerSimple.js file, much to no avail. I finally just copied the entire file you posted into a text file and saved it as .js in the scripts folder. Works great! :)

---

### Post by corticalaxon on 2008-07-15
Found the file, but gedit says I don't have the permission to save...what do I do? I'm logged in, with password, to my OS's only username...sorry...I'm a newbie...

---

