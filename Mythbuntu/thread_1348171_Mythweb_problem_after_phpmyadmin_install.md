---
title: "Mythweb problem after phpmyadmin install"
date: 2009-12-06
forum: Mythbuntu
---

### Post by wasko7 on 2009-12-06
I had a perfectly good install of Mythbuntu 9.10 until I installed phpmyadmin via synaptic. It installed with all of its dependancies. I ran through the install with the correct username and passwords, but it failed to log me in.    Sooo no problem just uninstall......  However since the failed install I cant access mythweb anymore.  I was able to access it once this morning but as I moused over the TV listings a small box came up in the bottom left hand corner of the page saying 1 reqest pending and as I moused over each listing the number of request pending rose accordingly. However since then I cannot access mythweb at all.
I get "Not Found" 
The requested URL /mythweb was not found on this server.
Apache/2.2.12(Ubuntu) Server at 192.168.1.22 Port 80

I've read a number of posts about phpmyadmin also using port 80 and was wondering if that would have anything to do with it and how I can fix this.  Thanks in advance.
B



Since this original post I have been able to access mythweb but it takes approx 1-2 minutes to appear and with these errors across the top of the page.

User Notice at /usr/share/mythtv/mythweb/classes/MythBackend.php, line 102:\par
Unexpected response to MYTH_PROTO_VERSION '50':"

"Warning at /usr/share/mythtv/mythweb/modules/_shared/tmpl/default/header.php, line 16:
Cannot modify header information - headers already sent by (output started at /usr/share/mythtv/mythweb/includes/errors.php:148 )

So Far I'm able to use the system but it is incredibly slow till finally I get a blank page with the above error messages plus this one:

"Warning at /usr/share/mythtv/mythweb/includes/utils.php, line 107:
Cannot modify header information - headers already sent by (output started at /usr/share/mythtv/mythweb/includes/errors.php:148 )"

 The text from the two php files is below:


** /usr/share/mythtv/mythweb/classes/MythBackend.php**

<?php
/**
 *
 * @url         $URL: [http://svn.mythtv.org/svn/branches/release-0-22-fixes/mythplugins/mythweb/classes/MythBackend.php](http://svn.mythtv.org/svn/branches/release-0-22-fixes/mythplugins/mythweb/classes/MythBackend.php) $
 * @date        $Date: 2009-10-02 00:48:08 -0500 (Fri, 02 Oct 2009) $
 * @version     $Revision: 22174 $
 * @author      $Author: robertm $
 * @license     GPL
 *
 * @package     MythTV
 *
/**/

class MythBackend {

// MYTH_PROTO_VERSION is defined in libmyth in mythtv/libs/libmyth/mythcontext.h
// and should be the current MythTV protocol version.
    static $protocol_version        = 50;

// The character string used by the backend to separate records
    static $backend_separator       = '[]:[]';

// NUMPROGRAMLINES is defined in mythtv/libs/libmythtv/programinfo.h and is
// the number of items in a ProgramInfo QStringList group used by
// ProgramInfo::ToSringList and ProgramInfo::FromStringList.
    static $program_line_number     = 47;

    private $fp                     = null;
    private $connected              = false;
    private $host                   = '127.0.0.1';
    private $ip                     = '127.0.0.1';
    private $port                   = null;
    private $port_http              = null;

    static function find($host = null, $port = null) {
        static $Backends = array();

    // Looking for the master backend?
        if (is_null($host)) {
            $host = setting('MasterServerIP');
            $port = setting('MasterServerPort');
            if (!$host || !$port)
                trigger_error("MasterServerIP or MasterServerPort not found! You may"
                            ."need to check your settings.php file or re-run mythtv-setup",
                            FATAL);
        }

        if (!isset($Backend[$host][$port]))
            $Backend[$host][$port] = new MythBackend($host, $port);
        return $Backend[$host][$port];
    }

    function __construct($host, $port = null) {
        $this->host         = $host;
        $this->ip           = _or(setting('BackendServerIP', $this->host), $host);
        $this->port         = _or($port, _or(setting('BackendServerPort', $this->host), 6543));
        $this->port_http    = _or(setting('BackendStatusPort', $this->host), _or(setting('BackendStatusPort'), 6544));
    }

    function __destruct() {
        $this->disconnect();
    }

    private function connect() {
        if ($this->fp)
            return;
        $this->fp = @fsockopen($this->ip, $this->port, $errno, $errstr, 25);
        if (!$this->fp)
            custom_error("Unable to connect to the master backend at {$this->ip}:{$this->port}".(($this->host == $this->ip)?'':" (hostname: {$this->host})").".\nIs it running?");
        socket_set_timeout($this->fp, 30);
        $this->checkProtocolVersion();
        $this->announce();
    }

    private function disconnect() {
        if (!$this->fp)
            return;
        $this->sendCommand('DONE');
        fclose($this->fp);
    }

    private function checkProtocolVersion() {
    // Allow overriding this check
        if ($_SERVER['ignore_proto'] == true )
            return true;

        if (   time() - $_SESSION['backend'][$this->host]['proto_version']['last_check_time'] < 60*60*2
            && $_SESSION['backend'][$this->host]['proto_version']['last_check_version'] == MythBackend::$protocol_version )
            return true;

        $response = $this->sendCommand('MYTH_PROTO_VERSION '.MythBackend::$protocol_version);
        $_SESSION['backend'][$this->host]['proto_version']['last_check_version'] = @$response[1];

        if ($response[0] == 'ACCEPT') {
            $_SESSION['backend'][$this->host]['proto_version']['last_check_time'] = time();
            return true;
        }

        if ($response[0] == 'REJECT')
            trigger_error("Incompatible protocol version (mythweb=" . MythBackend::$protocol_version . ", backend=" . @$response[1] . ")");
        else
            trigger_error("Unexpected response to MYTH_PROTO_VERSION '".MythBackend::$protocol_version."': ".print_r($response, true));
        return false;
    }

    private function announce() {
        $response = $this->sendCommand('ANN Monitor '.hostname.' 1' );
        if ($response == 'OK')
            return true;
        return false;
    }

    public function setTimezone() {
        if (!is_string($_SESSION['backend']['timezone']['value']) || $_SESSION['backend']['timezone']['last_check_time'] - time() > 60*60*24) {
            $response = $this->sendCommand('QUERY_TIME_ZONE');
            $timezone = str_replace(' ', '_', $response[0]);
            $_SESSION['backend']['timezone']['value']           = $timezone;
            $_SESSION['backend']['timezone']['last_check_time'] = time();
        }

        if (!@date_default_timezone_set($_SESSION['backend']['timezone']['value'])) {
            $attempted_value = $_SESSION['backend']['timezone']['value'];
            unset($_SESSION['backend']['timezone']);
            trigger_error('Failed to set php timezone to '.$attempted_value.(is_array($response) ? ' Response from backend was '.print_r($response, true) : ''));
        }
    }

    public function sendCommand($command = null) {
        $this->connect();
        if (is_array($command))
            $command = implode(MythBackend::$backend_separator, $command);
    // The format should be <length + whitespace to 8 total bytes><data>
        $command = strlen($command) . str_repeat(' ', 8 - strlen(strlen($command))) . $command;
        fputs($this->fp, $command);
        return $this->receiveData();
    }

    public function receiveData($timeout = 30) {
        $this->connect();
        stream_set_timeout($this->fp, $timeout);

    // Read the response header to find out how much data we'll be grabbing
        $length = rtrim(fread($this->fp, 8 ));

    // Read and return any data that was returned
        $response = '';
        while ($length > 0) {
            $data = fread($this->fp, min(8192, $length));
            if (strlen($data) < 1)
                break; // EOF
            $response .= $data;
            $length -= strlen($data);
        }
        $response = explode(MythBackend::$backend_separator, $response);
        if (count($response) == 1)
            return $response[0];
        if (count($response) == 0)
            return false;
        return $response;
    }

    public function listenForEvent($event, $timeout = 120) {
        $endtime = time() + $timeout;
        do {
            $response = $this->receiveData();
        } while ($response[1] != $event && $endtime < time());
        if ($response[1] == $event)
            return $response;
        return false;
    }

    public function queryProgramRows($query = null, $offset = 1) {
        $records = $this->sendCommand($query);
    // Parse the records, starting at the offset point
        $row = 0;
        $col = 0;
        $count = count($records);
        for($i = $offset; $i < $count; $i++) {
            $rows[$row][$col] = $records[$i];
        // Every $NUMPROGRAMLINES fields (0 through ($NUMPROGRAMLINES-1)) means
        // a new row.  Please note that this changes between myth versions
            if ($col == (MythBackend::$program_line_number - 1)) {
                $col = 0;
                $row++;
            }
        // Otherwise, just increment the column
            else
                $col++;
        }
    // Lastly, grab the offset data (if there is any)
        for ($i=0; $i < $offset; $i++) {
            $rows['offset'][$i] = $recs[$i];
        }
    // Return the data
        return $rows;
    }

/**
 * Tell the backend to reschedule a particular record entry.  If the change
 * isn't specific to a single record entry (e.g. channel or record type
 * priorities), then use 0.  I don't think mythweb should need it, but if you
 * need to indicate every record rule is affected, then use -1.
/**/
    public function rescheduleRecording($recordid = -1) {
        $this->sendCommand('RESCHEDULE_RECORDINGS '.$recordid);
        if ($this->listenForEvent('SCHEDULE_CHANGE'))
            return true;
        return false;
    }

    public function httpRequest($path, $args = array()) {
        $url = "http://{$this->ip}:{$this->port_http}/Myth/{$path}?";
        foreach ($args as $key => $value)
            $url .= $key.'='.urlencode($value).'&';
        return @file_get_contents($url);
    }
}

**/usr/share/mythtv/mythweb/modules/_shared/tmpl/default/Header.php**


<?php
/**
 * This header file is shared by all MythWeb modules.
 *
 * @url         $URL: [http://svn.mythtv.org/svn/branches/release-0-22-fixes/mythplugins/mythweb/modules/_shared/tmpl/default/header.php](http://svn.mythtv.org/svn/branches/release-0-22-fixes/mythplugins/mythweb/modules/_shared/tmpl/default/header.php) $
 * @date        $Date: 2009-08-01 23:50:00 -0500 (Sat, 01 Aug 2009) $
 * @version     $Revision: 21099 $
 * @author      $Author: kormoc $
 * @license     GPL
 *
 * @package     MythWeb
 *
/**/

// UTF-8 content
    header("Content-Type: text/html; charset=utf-8");

// Globals
    global $headers, $page_title;

// Create the category legend popup and stick it at the end of the document for now.
    global $Categories;
    if (!empty($Categories)) {
        $legend = <<<EOF
<table width="400" style="background-color: #003060;" border="1" cellpadding="0" cellspacing="0">
<tr>
    <td><table width="400" style="background-color: #003060;" class="small" cellpadding="5" cellspacing="5">
        <tr>
EOF;
        $legend .= "\t\t\t<td colspan=\"3\">".t('Category Legend').':</td>';
        $count = 0;
        foreach ($Categories as $cat => $details) {
            if ($count++ % 3 == 0)
                $legend .= "\n\t\t</tr><tr>\n";
            $legend .= "\t\t\t<td class=\"cat_$cat\" align=\"center\"><b>".html_entities($details[0])."</b></td>\n";
        }
        $legend .= <<<EOF
        </tr>
        </table></td>
</tr>
</table>
EOF;
    }

?>
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<html>
<head>
    <base href="<?php echo root_url; ?>">
    <title><?php echo html_entities($page_title) ?></title>

    <link rel="icon"          href="<?php echo skin_url ?>img/favicon.ico" type="image/x-icon">
    <link rel="shortcut icon" href="<?php echo skin_url ?>img/favicon.ico" type="image/x-icon">

    <link type="application/opensearchdescription+xml" rel="search" href="tv/opensearch?type=xml" title="MythTV">

    <meta http-equiv="content-type" content="text/html; charset=utf-8">
    <meta name="robots" content="noindex, nofollow">

    <script type="text/javascript" src="js/prototype.js"></script>
    <script type="text/javascript" src="js/prototip/prototip.js"></script>
    <link rel="stylesheet" type="text/css" href="js/prototip/prototip.css">

    <script type="text/javascript" src="js/utils.js"></script>
    <script type="text/javascript" src="js/AC_OETags.js"></script>
    <script type="text/javascript" src="js/table_sort.js"></script>

    <script type="text/javascript">
        <!--
        // -----------------------------------------------------------------------------
        // Globals
        // Major version of Flash required
        var requiredMajorVersion = 9;
        // Minor version of Flash required
        var requiredMinorVersion = 0;
        // Minor version of Flash required
        var requiredRevision = 0;
        // -----------------------------------------------------------------------------
        // -->
    </script>

    <link rel="stylesheet" type="text/css" href="<?php echo skin_url ?>/style.css">
    <link rel="stylesheet" type="text/css" href="<?php echo skin_url ?>/header.css">
    <link rel="stylesheet" type="text/css" href="<?php echo skin_url ?>/menus.css">
    <link rel="stylesheet" type="text/css" href="<?php echo skin_url ?>/programming.css">

<?php
    if (!empty($headers) && is_array($headers))
        echo '    ', implode("\n    ", $headers), "\n";
?>

</head>

<body>

<div id="page_header" class="clearfix">
    <div id="logo_box">
        <a id="mythtv_logo" href="<?php echo root_url; ?>">
        <img src="<?php echo skin_url ?>img/mythtv-logo.png" alt="MythTV" class="alpha_png">
        </a>
    </div>
    <div id="sections">
<?php
    if (Modules::getModule('tv')) {
?>
        <a id="tv_link"<?php if ($Path[0] == 'tv') echo ' class="current_section"' ?> href="tv" onmouseover="return help_text('<?php echo str_replace("'", "\\'", t('TV functions, including recorded programs.')) ?>')" onmouseout="return help_text()">
            <img src="<?php echo skin_url ?>img/tv.png" class="alpha_png" alt="MythTV">
        </a>
<?php
    }
    if (Modules::getModule('music')) {
?>
        <a id="music_link"<?php if ($Path[0] == 'music') echo ' class="current_section"' ?> href="music" onmouseover="return help_text('<?php echo str_replace("'", "\\'", t('MythMusic on the web.')) ?>')" onmouseout="return help_text()">
            <img src="<?php echo skin_url ?>img/music.png" class="alpha_png" alt="MythMusic">
        </a>
<?php
      }
      if (Modules::getModule('video')) {
?>
        <a id="video_link"<?php if ($Path[0] == 'video') echo ' class="current_section"' ?> href="video" onmouseover="return help_text('<?php echo str_replace("'", "\\'", t('MythVideo on the web.')) ?>')" onmouseout="return help_text()">
            <img src="<?php echo skin_url ?>img/video.png" class="alpha_png" alt="MythVideo">
        </a>
<?php
      }
      if (Modules::getModule('weather')) {
?>
        <a id="weather_link"<?php if ($Path[0] == 'weather') echo ' class="current_section"' ?> href="weather" onmouseover="return help_text('<?php echo str_replace("'", "\\'", t('MythWeb Weather.')) ?>')" onmouseout="return help_text()">
            <img src="<?php echo skin_url ?>img/weather.png" class="alpha_png" alt="MythWeather">
        </a>
<?php
      }
?>
        <a id="settings_link"<?php if ($Path[0] == 'settings') echo ' class="current_section"' ?> href="settings" onmouseover="return help_text('<?php echo str_replace("'", "\\'", t('Edit MythWeb and some MythTV settings.')) ?>')" onmouseout="return help_text()">
            <img src="<?php echo skin_url ?>img/settings.png" class="alpha_png" alt="<?php echo t('Settings') ?>">
        </a>
    </div>
    <div id="extra_header">
        <div id="help_wrapper">
            <div id="help_box">
                <div id="help_text_default" style="position:relative;">
                MythWeb: <?php echo strftime($_SESSION['date_statusbar'], time()) ?>
                </div>
                <div id="help_text" style="display:none;">
                </div>
            </div>
        </div>
        <?php if (Modules::getModule('tv')) { ?>
        <div id="search">
            <form action="tv/search" method="get">
                <div id="simple_search">
                    <input type="hidden" name="type" value="q">
                    <input id="search_text" type="text" name="s" size="15" value="<?php echo html_entities($_SESSION['search']['s']) ?>">
                    <input id="search_submit" type="submit" class="submit" name="search" value="<?php echo t('Search') ?>">
                    (<a href="tv/search"><?php echo t('Advanced') ?></a>)
                </div>
            </form>
        </div>
        <?php } ?>
    </div>
</div>


<table width="100%" border="0" cellspacing="2" cellpadding="0">
<tr>

    <td colspan="2" class="menu menu_border_t menu_border_b"><table class="body" width="100%" border="0" cellspacing="2" cellpadding="2">
        <tr>
            <td><div id="command_choices">
                    <a href="" <?php
                        echo show_popup('category_legend',$legend)
                        ?>>MythTV:</a> &nbsp; &nbsp;
                    <?php if (Modules::getModule('tv')) { ?>
                        <a href="tv/list"><?php echo t('Listings') ?></a>
                        &nbsp; | &nbsp;
                        <a href="tv/searches"><?php echo t('Searches') ?></a>
                        &nbsp; | &nbsp;
                        <a href="tv/schedules"><?php echo t('Recording Schedules') ?></a>
                        (<a href="tv/schedules/manual"><?php echo t('Manual') ?></a>,
                        <a href="tv/schedules/custom"><?php echo t('Custom') ?></a>)
                        &nbsp; | &nbsp;
                        <a href="tv/upcoming"><?php echo t('Upcoming Recordings') ?></a>
                        &nbsp; | &nbsp;
                        <a href="tv/recorded"><?php echo t('Recorded Programs') ?></a>
                        &nbsp; | &nbsp;
                    <?php } ?>
                    <a href="status"><?php echo t('Backend Status') ?></a>
<?php if (Modules::getModule('backend_log')) { ?>
                    &nbsp; | &nbsp;
                    <a href="backend_log"><?php echo t('Backend Logs') ?></a>
<?php } ?>
                </div></td>
        </tr>
        </table></td>

</tr>
</table>

<?php
// Errors go here
    display_errors();

---

