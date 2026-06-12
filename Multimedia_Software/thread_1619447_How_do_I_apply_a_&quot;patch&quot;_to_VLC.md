---
title: "How do I apply a &quot;patch&quot; to VLC?"
date: 2010-11-11
forum: Multimedia Software
---

### Post by hurtstotalktoyou on 2010-11-11
I'm running Ubuntu 10.04 64-bit, and I'd like to apply the following "patch" to VLC:

[http://forum.videolan.org/viewtopic.php?f=12&t=46020#p256565](http://forum.videolan.org/viewtopic.php?f=12&t=46020#p256565)

```
    diff -purN vlc.orig/modules/audio_filter/compressor.c vlc/modules/audio_filter/compressor.c
    --- vlc.orig/modules/audio_filter/compressor.c   1969-12-31 18:00:00.000000000 -0600
    +++ vlc/modules/audio_filter/compressor.c   2010-06-19 13:17:53.934683044 -0500
    @@ -0,0 +1,826 @@
    +/*****************************************************************************
    + * compressor.c: dynamic range compressor, ported from SC4 plugin
    + *****************************************************************************
    + *
    + * Authors: Ronald Wright <logiconcepts819@gmail.com>
    + * Original authors: Steve Harris <steve@plugin.org.uk>
    + *
    + * This program is free software; you can redistribute it and/or modify
    + * it under the terms of the GNU General Public License as published by
    + * the Free Software Foundation; either version 2 of the License, or
    + * (at your option) any later version.
    + *
    + * This program is distributed in the hope that it will be useful,
    + * but WITHOUT ANY WARRANTY; without even the implied warranty of
    + * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    + * GNU General Public License for more details.
    + *
    + * You should have received a copy of the GNU General Public License
    + * along with this program; if not, write to the Free Software
    + * Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston MA 02110-1301, USA.
    + *****************************************************************************/
    +
    +/*****************************************************************************
    + * Preamble
    + *****************************************************************************/
    +
    +#ifdef HAVE_CONFIG_H
    +# include "config.h"
    +#endif
    +
    +#include <math.h>
    +#include <stdint.h>
    +
    +#include <vlc_common.h>
    +#include <vlc_plugin.h>
    +
    +#include <vlc_aout.h>
    +#include <vlc_filter.h>
    +
    +/*****************************************************************************
    +* Local prototypes.
    +*****************************************************************************/
    +
    +#define A_TBL (256)
    +
    +#define DB_TABLE_SIZE   (1024)
    +#define DB_MIN          (-60.0f)
    +#define DB_MAX          (24.0f)
    +#define LIN_TABLE_SIZE  (1024)
    +#define LIN_MIN         (0.0000000002f)
    +#define LIN_MAX         (9.0f)
    +
    +#define DB_DEFAULT_CUBE
    +
    +#ifdef DB_DEFAULT_CUBE
    +#define db2lin(a,b) (f_db2lin_cube(a,b))
    +#define lin2db(a,b) (f_lin2db_cube(a,b))
    +#else
    +#define db2lin(a,b) (f_db2lin_lerp(a,b))
    +#define lin2db(a,b) (f_lin2db_lerp(a,b))
    +#endif
    +
    +#define RMS_BUF_SIZE    (64)
    +
    +#define LIN_INTERP(f,a,b) ((a) + (f) * ( (b) - (a) ))
    +
    +typedef struct
    +{
    +    float        buffer[RMS_BUF_SIZE];
    +    unsigned int pos;
    +    float        sum;
    +} rms_env;
    +
    +struct filter_sys_t
    +{
    +    float rms_peak;
    +    float attack;
    +    float release;
    +    float threshold;
    +    float ratio;
    +    float knee;
    +    float makeup_gain;
    +    float amplitude;
    +    float gain_red;
    +
    +    float amp;
    +    float *as;
    +    unsigned int count;
    +    float env;
    +    float env_peak;
    +    float env_rms;
    +    float gain;
    +    float gain_t;
    +    rms_env* rms;
    +    float sum;
    +
    +    float db_data[DB_TABLE_SIZE];
    +    float lin_data[LIN_TABLE_SIZE];
    +
    +    vlc_mutex_t lock;
    +};
    +
    +typedef union
    +{
    +    float f;
    +    int32_t i;
    +} ls_pcast32;
    +
    +static int      Open            ( vlc_object_t * );
    +static void     Close           ( vlc_object_t * );
    +static void     db_init         ( filter_sys_t * p_sys );
    +static float    f_db2lin_cube   ( float db, filter_sys_t * p_sys );
    +static float    f_db2lin_lerp   ( float db, filter_sys_t * p_sys );
    +static float    f_lin2db_cube   ( float lin, filter_sys_t * p_sys );
    +static float    f_lin2db_lerp   ( float lin, filter_sys_t * p_sys );
    +static void     round_to_zero   ( volatile float *f );
    +static float    f_max           ( float x, float a );
    +static int      f_round         ( float f );
    +static float    cube_interp     ( const float fr, const float inm1,
    +                                                  const float in,
    +                                                  const float inp1,
    +                                                  const float inp2 );
    +static rms_env *rms_env_new     ( void );
    +static float    rms_env_process ( rms_env * r, const float x );
    +static void     rms_env_free    ( rms_env * r );
    +static block_t *DoWork          ( filter_t *, block_t * );
    +
    +static int RMSPeakCallback      ( vlc_object_t *p_this, char const *psz_cmd,
    +                                  vlc_value_t oldval, vlc_value_t newval,
    +                                  void * p_data );
    +static int AttackCallback       ( vlc_object_t *p_this, char const *psz_cmd,
    +                                  vlc_value_t oldval, vlc_value_t newval,
    +                                  void * p_data );
    +static int ReleaseCallback      ( vlc_object_t *p_this, char const *psz_cmd,
    +                                  vlc_value_t oldval, vlc_value_t newval,
    +                                  void * p_data );
    +static int ThresholdCallback    ( vlc_object_t *p_this, char const *psz_cmd,
    +                                  vlc_value_t oldval, vlc_value_t newval,
    +                                  void * p_data );
    +static int RatioCallback        ( vlc_object_t *p_this, char const *psz_cmd,
    +                                  vlc_value_t oldval, vlc_value_t newval,
    +                                  void * p_data );
    +static int KneeCallback         ( vlc_object_t *p_this, char const *psz_cmd,
    +                                  vlc_value_t oldval, vlc_value_t newval,
    +                                  void * p_data );
    +static int MakeupGainCallback   ( vlc_object_t *p_this, char const *psz_cmd,
    +                                  vlc_value_t oldval, vlc_value_t newval,
    +                                  void * p_data );
    +
    +/*****************************************************************************
    + * Module descriptor
    + *****************************************************************************/
    +
    +#define RMS_PEAK_TEXT N_( "RMS/peak" )
    +#define RMS_PEAK_LONGTEXT N_( "Set the RMS/peak (0 ... 1)." )
    +
    +#define ATTACK_TEXT N_( "Attack time" )
    +#define ATTACK_LONGTEXT N_( \
    +        "Set the attack time in milliseconds (1.5 ... 400)." )
    +
    +#define RELEASE_TEXT N_( "Release time" )
    +#define RELEASE_LONGTEXT N_( \
    +        "Set the release time in milliseconds (2 ... 800)." )
    +
    +#define THRESHOLD_TEXT N_( "Threshold level" )
    +#define THRESHOLD_LONGTEXT N_( "Set the threshold level in dB (-30 ... 0)." )
    +
    +#define RATIO_TEXT N_( "Ratio" )
    +#define RATIO_LONGTEXT N_( "Set the ratio (n:1) (1 ... 20)." )
    +
    +#define KNEE_TEXT N_( "Knee radius" )
    +#define KNEE_LONGTEXT N_( "Set the knee radius in dB (1 ... 10)." )
    +
    +#define MAKEUP_GAIN_TEXT N_( "Makeup gain" )
    +#define MAKEUP_GAIN_LONGTEXT N_( "Set the makeup gain in dB (0 ... 24)." )
    +
    +vlc_module_begin()
    +    set_shortname( _("Compressor") )
    +    set_description( _("Dynamic range compressor") )
    +    set_capability( "audio filter", 0 )
    +    set_category( CAT_AUDIO )
    +    set_subcategory( SUBCAT_AUDIO_AFILTER )
    +
    +    add_float( "compressor-rms-peak", 0.0, NULL, RMS_PEAK_TEXT,
    +               RMS_PEAK_LONGTEXT, false )
    +    add_float( "compressor-attack", 1.5, NULL, ATTACK_TEXT,
    +               ATTACK_LONGTEXT, false )
    +    add_float( "compressor-release", 800.0, NULL, RELEASE_TEXT,
    +               RELEASE_LONGTEXT, false )
    +    add_float( "compressor-threshold", -11.0, NULL, THRESHOLD_TEXT,
    +               THRESHOLD_LONGTEXT, false )
    +    add_float( "compressor-ratio", 10.0, NULL, RATIO_TEXT,
    +               RATIO_LONGTEXT, false )
    +    add_float( "compressor-knee", 1.0, NULL, KNEE_TEXT,
    +               KNEE_LONGTEXT, false )
    +    add_float( "compressor-makeup-gain", 10.0, NULL, MAKEUP_GAIN_TEXT,
    +               MAKEUP_GAIN_LONGTEXT, false )
    +    set_callbacks( Open, Close )
    +    add_shortcut( "compressor" )
    +vlc_module_end ()
    +
    +/*****************************************************************************
    + * Open: initialize interface
    + *****************************************************************************/
    +
    +static int Open( vlc_object_t *p_this )
    +{
    +    filter_t *p_filter = (filter_t*)p_this;
    +    vlc_object_t *p_aout = p_filter->p_parent;
    +    struct filter_sys_t *p_sys;
    +    float amp;
    +    float *as = NULL;
    +    unsigned int count;
    +    float env;
    +    float env_peak;
    +    float env_rms;
    +    float gain;
    +    float gain_t;
    +    rms_env *rms = NULL;
    +    float sum;
    +
    +    unsigned int i;
    +    float sample_rate;
    +
    +    if ( p_filter->fmt_in.audio.i_format != VLC_CODEC_FL32 ||
    +         p_filter->fmt_out.audio.i_format != VLC_CODEC_FL32 )
    +    {
    +        p_filter->fmt_in.audio.i_format = VLC_CODEC_FL32;
    +        p_filter->fmt_out.audio.i_format = VLC_CODEC_FL32;
    +        msg_Warn( p_filter, "bad input or output format" );
    +        return VLC_EGENERIC;
    +    }
    +    if ( !AOUT_FMTS_SIMILAR( &p_filter->fmt_in.audio,
    +                             &p_filter->fmt_out.audio ) )
    +    {
    +        memcpy( &p_filter->fmt_out.audio, &p_filter->fmt_in.audio,
    +                sizeof(audio_sample_format_t) );
    +        msg_Warn( p_filter, "input and output formats are not similar" );
    +        return VLC_EGENERIC;
    +    }
    +
    +    sample_rate = (float)p_filter->fmt_in.audio.i_rate;
    +
    +    p_filter->pf_audio_filter = DoWork;
    +
    +    p_sys = p_filter->p_sys = malloc( sizeof( *p_sys ) );
    +    if ( !p_sys )
    +    {
    +        return VLC_ENOMEM;
    +    }
    +
    +    rms = rms_env_new();
    +    if ( !rms )
    +    {
    +        free( p_sys );
    +        return VLC_ENOMEM;
    +    }
    +
    +    sum = 0.0f;
    +    amp = 0.0f;
    +    gain = 0.0f;
    +    gain_t = 0.0f;
    +    env = 0.0f;
    +    env_rms = 0.0f;
    +    env_peak = 0.0f;
    +    count = 0;
    +
    +    as = malloc( A_TBL * sizeof(float) );
    +    if ( !as )
    +    {
    +        rms_env_free( rms );
    +        free( p_sys );
    +        return VLC_ENOMEM;
    +    }
    +
    +    as[0] = 1.0f;
    +    for ( i = 1; i < A_TBL; i++ ) {
    +        as[i] = expf( -1.0f / ( sample_rate * (float)i / (float)A_TBL ) );
    +    }
    +
    +    db_init( p_sys );
    +
    +    p_sys->amp = amp;
    +    p_sys->as = as;
    +    p_sys->count = count;
    +    p_sys->env = env;
    +    p_sys->env_peak = env_peak;
    +    p_sys->env_rms = env_rms;
    +    p_sys->gain = gain;
    +    p_sys->gain_t = gain_t;
    +    p_sys->rms = rms;
    +    p_sys->sum = sum;
    +
    +    vlc_mutex_init( &p_sys->lock );
    +
    +    p_sys->rms_peak    = var_CreateGetFloat( p_aout, "compressor-rms-peak" );
    +    p_sys->attack      = var_CreateGetFloat( p_aout, "compressor-attack" );
    +    p_sys->release     = var_CreateGetFloat( p_aout, "compressor-release" );
    +    p_sys->threshold   = var_CreateGetFloat( p_aout, "compressor-threshold" );
    +    p_sys->ratio       = var_CreateGetFloat( p_aout, "compressor-ratio" );
    +    p_sys->knee        = var_CreateGetFloat( p_aout, "compressor-knee" );
    +    p_sys->makeup_gain = var_CreateGetFloat( p_aout, "compressor-makeup-gain" );
    +    p_sys->amplitude   = 0;
    +    p_sys->gain_red    = 0;
    +
    +    /* Add our own callbacks */
    +    var_AddCallback( p_aout, "compressor-rms-peak", RMSPeakCallback, p_sys );
    +    var_AddCallback( p_aout, "compressor-attack", AttackCallback, p_sys );
    +    var_AddCallback( p_aout, "compressor-release", ReleaseCallback, p_sys );
    +    var_AddCallback( p_aout, "compressor-threshold", ThresholdCallback, p_sys );
    +    var_AddCallback( p_aout, "compressor-ratio", RatioCallback, p_sys );
    +    var_AddCallback( p_aout, "compressor-knee", KneeCallback, p_sys );
    +    var_AddCallback( p_aout, "compressor-makeup-gain", MakeupGainCallback,
    +                     p_sys );
    +
    +    msg_Dbg( p_filter, "compressor successfully initialized" );
    +    return VLC_SUCCESS;
    +}
    +
    +/*****************************************************************************
    + * Close: destroy interface
    + *****************************************************************************/
    +
    +static void Close( vlc_object_t *p_this )
    +{
    +    filter_t *p_filter = (filter_t*)p_this;
    +    vlc_object_t *p_aout = p_filter->p_parent;
    +    struct filter_sys_t *p_sys = p_filter->p_sys;
    +
    +    var_DelCallback( p_aout, "compressor-rms-peak", RMSPeakCallback, p_sys );
    +    var_DelCallback( p_aout, "compressor-attack", AttackCallback, p_sys );
    +    var_DelCallback( p_aout, "compressor-release", ReleaseCallback, p_sys );
    +    var_DelCallback( p_aout, "compressor-threshold", ThresholdCallback, p_sys );
    +    var_DelCallback( p_aout, "compressor-ratio", RatioCallback, p_sys );
    +    var_DelCallback( p_aout, "compressor-knee", KneeCallback, p_sys );
    +    var_DelCallback( p_aout, "compressor-makeup-gain", MakeupGainCallback,
    +                     p_sys );
    +
    +    vlc_mutex_destroy( &p_sys->lock );
    +
    +    rms_env_free( p_sys->rms );
    +    free( p_sys->as );
    +    free( p_sys );
    +}
    +
    +/*****************************************************************************
    + * Helper functions for compressor
    + *****************************************************************************/
    +
    +static void db_init( filter_sys_t * p_sys )
    +{
    +    unsigned int i;
    +    float *lin_data = p_sys->lin_data;
    +    float *db_data = p_sys->db_data;
    +
    +    for ( i = 0; i < LIN_TABLE_SIZE; i++ )
    +    {
    +        lin_data[i] = powf( 10.0f, ( ( DB_MAX - DB_MIN ) *
    +                (float)i / (float)LIN_TABLE_SIZE + DB_MIN ) / 20.0f );
    +    }
    +
    +    for ( i = 0; i < DB_TABLE_SIZE; i++ )
    +    {
    +        db_data[i] = 20.0f * log10f( ( LIN_MAX - LIN_MIN ) *
    +                (float)i / (float)DB_TABLE_SIZE + LIN_MIN );
    +    }
    +}
    +
    +static float f_db2lin_cube( float db, filter_sys_t * p_sys )
    +{
    +    float scale = ( db - DB_MIN ) * (float)LIN_TABLE_SIZE / ( DB_MAX - DB_MIN );
    +    int base = f_round( scale - 0.5f );
    +    float ofs = scale - base;
    +    float *lin_data = p_sys->lin_data;
    +
    +    if ( base < 1 )
    +    {
    +        return 0.0f;
    +    }
    +    else if ( base > LIN_TABLE_SIZE - 3 )
    +    {
    +        return lin_data[LIN_TABLE_SIZE - 2];
    +    }
    +
    +    return cube_interp( ofs, lin_data[base - 1],
    +                             lin_data[base],
    +                             lin_data[base + 1],
    +                             lin_data[base + 2] );
    +}
    +
    +static float f_db2lin_lerp( float db, filter_sys_t * p_sys )
    +{
    +    float scale = ( db - DB_MIN ) * (float)LIN_TABLE_SIZE / ( DB_MAX - DB_MIN );
    +    int base = f_round( scale - 0.5f );
    +    float ofs = scale - base;
    +    float *lin_data = p_sys->lin_data;
    +
    +    if ( base < 1 )
    +    {
    +        return 0.0f;
    +    }
    +    else if ( base > LIN_TABLE_SIZE - 3 )
    +    {
    +        return lin_data[LIN_TABLE_SIZE - 2];
    +    }
    +
    +    return ( 1.0f - ofs ) * lin_data[base] + ofs * lin_data[base + 1];
    +}
    +
    +static float f_lin2db_cube( float lin, filter_sys_t * p_sys )
    +{
    +    float scale = ( lin - LIN_MIN ) * (float)DB_TABLE_SIZE /
    +        ( LIN_MAX - LIN_MIN );
    +    int base = f_round( scale - 0.5f );
    +    float ofs = scale - base;
    +    float *db_data = p_sys->db_data;
    +
    +    if ( base < 2 )
    +    {
    +        return db_data[2] * scale * 0.5f - 23.0f * ( 2.0f - scale );
    +    }
    +    else if ( base > DB_TABLE_SIZE - 3 )
    +    {
    +        return db_data[DB_TABLE_SIZE - 2];
    +    }
    +
    +    return cube_interp( ofs, db_data[base - 1],
    +                             db_data[base],
    +                             db_data[base + 1],
    +                             db_data[base + 2] );
    +}
    +
    +static float f_lin2db_lerp( float lin, filter_sys_t * p_sys )
    +{
    +    float scale = ( lin - LIN_MIN ) * (float)DB_TABLE_SIZE /
    +        ( LIN_MAX - LIN_MIN );
    +    int base = f_round( scale - 0.5f );
    +    float ofs = scale - base;
    +    float *db_data = p_sys->db_data;
    +
    +    if ( base < 2 )
    +    {
    +        return db_data[2] * scale * 0.5f - 23.0f * ( 2.0f - scale );
    +    }
    +    else if ( base > DB_TABLE_SIZE - 2 )
    +    {
    +        return db_data[DB_TABLE_SIZE - 1];
    +    }
    +
    +    return ( 1.0f - ofs ) * db_data[base] + ofs * db_data[base + 1];
    +}
    +
    +static void round_to_zero( volatile float *f )
    +{
    +    *f += 1e-18;
    +    *f -= 1e-18;
    +}
    +
    +static float f_max( float x, float a )
    +{
    +    x -= a;
    +    x += fabs( x );
    +    x *= 0.5;
    +    x += a;
    +
    +    return x;
    +}
    +
    +static int f_round( float f )
    +{
    +    ls_pcast32 p;
    +
    +    p.f = f;
    +    p.f += ( 3 << 22 );
    +
    +    return p.i - 0x4b400000;
    +}
    +
    +static float cube_interp( const float fr, const float inm1, const float in,
    +                                          const float inp1, const float inp2 )
    +{
    +    return in + 0.5f * fr * ( inp1 - inm1 +
    +         fr * ( 4.0f * inp1 + 2.0f * inm1 - 5.0f * in - inp2 +
    +         fr * ( 3.0f * ( in - inp1 ) - inm1 + inp2 ) ) );
    +}
    +
    +static rms_env * rms_env_new( void )
    +{
    +    rms_env *new = (rms_env *)calloc( 1, sizeof(rms_env) );
    +    return new;
    +}
    +
    +static float rms_env_process( rms_env * r, const float x )
    +{
    +    r->sum -= r->buffer[r->pos];
    +    r->sum += x;
    +    if ( r->sum < 1.0e-6 )
    +    {
    +        r->sum = 0.0f;
    +    }
    +    r->buffer[r->pos] = x;
    +    r->pos = ( r->pos + 1 ) & ( RMS_BUF_SIZE - 1 );
    +
    +    return sqrt( r->sum / (float)RMS_BUF_SIZE );
    +}
    +
    +static void rms_env_free( rms_env * r )
    +{
    +    free( r );
    +}
    +
    +/*****************************************************************************
    + * DoWork: process samples buffer
    + *****************************************************************************/
    +
    +static block_t * DoWork( filter_t * p_filter, block_t * p_in_buf )
    +{
    +    int i_samples = p_in_buf->i_nb_samples;
    +    int i_channels = aout_FormatNbChannels( &p_filter->fmt_in.audio );
    +    float *p_out = (float*)p_in_buf->p_buffer;
    +    float *p_in =  (float*)p_in_buf->p_buffer;
    +
    +    float rms_peak, attack, release, threshold, ratio, knee, makeup_gain;
    +    float amp, *as, env, env_peak, env_rms, gain, gain_t, sum;
    +    unsigned int count;
    +    rms_env *rms;
    +
    +    float ga, gr, rs, mug, knee_min, knee_max, ef_a, ef_ai;
    +
    +    int pos, pos_chan;
    +
    +    /* Current configuration */
    +    struct filter_sys_t *p_sys = p_filter->p_sys;
    +
    +    vlc_mutex_lock( &p_sys->lock );
    +
    +    /* RMS/peak (float value) */
    +    rms_peak = p_sys->rms_peak;
    +
    +    /* Attack time (ms) (float value) */
    +    attack = p_sys->attack;
    +
    +    /* Release time (ms) (float value) */
    +    release = p_sys->release;
    +
    +    /* Threshold level (dB) (float value) */
    +    threshold = p_sys->threshold;
    +
    +    /* Ratio (n:1) (float value) */
    +    ratio = p_sys->ratio;
    +
    +    /* Knee radius (dB) (float value) */
    +    knee = p_sys->knee;
    +
    +    /* Makeup gain (dB) (float value) */
    +    makeup_gain = p_sys->makeup_gain;
    +
    +    amp = p_sys->amp;
    +    as = p_sys->as;
    +    count = p_sys->count;
    +    env = p_sys->env;
    +    env_peak = p_sys->env_peak;
    +    env_rms = p_sys->env_rms;
    +    gain = p_sys->gain;
    +    gain_t = p_sys->gain_t;
    +    rms = p_sys->rms;
    +    sum = p_sys->sum;
    +
    +    ga = attack < 2.0f ? 0.0f
    +                       : as[f_round( attack * 0.001f * (float)( A_TBL - 1 ) )];
    +    gr = as[f_round( release * 0.001f * (float)( A_TBL - 1 ) )];
    +    rs = ( ratio - 1.0f ) / ratio;
    +    mug = db2lin( makeup_gain, p_sys );
    +    knee_min = db2lin( threshold - knee, p_sys );
    +    knee_max = db2lin( threshold + knee, p_sys );
    +    ef_a = ga * 0.25f;
    +    ef_ai = 1.0f - ef_a;
    +
    +    for ( pos = 0; pos < i_samples; pos++ )
    +    {
    +        float lev_in = fabs( p_in[0] );
    +        for( pos_chan = 1; pos_chan < i_channels; pos_chan++ )
    +        {
    +            lev_in = f_max( lev_in, fabs( p_in[pos_chan] ) );
    +        }
    +        sum += lev_in * lev_in;
    +
    +        if ( amp > env_rms )
    +        {
    +            env_rms = env_rms * ga + amp * ( 1.0f - ga );
    +        }
    +        else
    +        {
    +            env_rms = env_rms * gr + amp * ( 1.0f - gr );
    +        }
    +        round_to_zero( &env_rms );
    +        if ( lev_in > env_peak )
    +        {
    +            env_peak = env_peak * ga + lev_in * ( 1.0f - ga );
    +        }
    +        else
    +        {
    +            env_peak = env_peak * gr + lev_in * ( 1.0f - gr );
    +        }
    +        round_to_zero( &env_peak );
    +        if ( ( count++ & 3 ) == 3 )
    +        {
    +            amp = rms_env_process( rms, sum * 0.25f );
    +            sum = 0.0f;
    +            if ( isnan( env_rms ) )
    +            {
    +                /* This can happen sometimes, but I don't know why */
    +                env_rms = 0.0f;
    +            }
    +
    +            env = LIN_INTERP( rms_peak, env_rms, env_peak );
    +
    +            if ( env <= knee_min )
    +            {
    +                gain_t = 1.0f;
    +            }
    +            else if ( env < knee_max )
    +            {
    +                const float x = -( threshold - knee
    +                                             - lin2db( env, p_sys ) ) / knee;
    +                gain_t = db2lin( -knee * rs * x * x * 0.25f, p_sys );
    +            }
    +            else
    +            {
    +                gain_t = db2lin( ( threshold - lin2db( env, p_sys ) ) * rs,
    +                                 p_sys );
    +            }
    +        }
    +
    +        gain = gain * ef_a + gain_t * ef_ai;
    +
    +        for ( pos_chan = 0; pos_chan < i_channels; pos_chan++ )
    +        {
    +            p_out[pos_chan] = p_in[pos_chan] * gain * mug;
    +        }
    +
    +        p_in  += i_channels;
    +        p_out += i_channels;
    +    }
    +
    +    p_sys->sum = sum;
    +    p_sys->amp = amp;
    +    p_sys->gain = gain;
    +    p_sys->gain_t = gain_t;
    +    p_sys->env = env;
    +    p_sys->env_rms = env_rms;
    +    p_sys->env_peak = env_peak;
    +    p_sys->count = count;
    +
    +    p_sys->amplitude = lin2db( env, p_sys );
    +    p_sys->gain_red = lin2db( gain, p_sys );
    +
    +    vlc_mutex_unlock( &p_sys->lock );
    +
    +    return p_in_buf;
    +}
    +
    +/*****************************************************************************
    + * Callback functions
    + *****************************************************************************/
    +
    +static int RMSPeakCallback( vlc_object_t *p_this, char const *psz_cmd,
    +                            vlc_value_t oldval, vlc_value_t newval,
    +                            void * p_data )
    +{
    +    VLC_UNUSED(p_this); VLC_UNUSED(psz_cmd); VLC_UNUSED(oldval);
    +    filter_sys_t *p_sys = p_data;
    +   
    +    if ( newval.f_float < 0.0 )
    +    {
    +        newval.f_float = 0.0;
    +    }
    +    else if ( newval.f_float > 1.0 )
    +    {
    +        newval.f_float = 1.0;
    +    }
    +
    +    vlc_mutex_lock( &p_sys->lock );
    +    p_sys->rms_peak = newval.f_float;
    +    vlc_mutex_unlock( &p_sys->lock );
    +
    +    return VLC_SUCCESS;
    +}
    +
    +static int AttackCallback( vlc_object_t *p_this, char const *psz_cmd,
    +                           vlc_value_t oldval, vlc_value_t newval,
    +                           void * p_data )
    +{
    +    VLC_UNUSED(p_this); VLC_UNUSED(psz_cmd); VLC_UNUSED(oldval);
    +    filter_sys_t *p_sys = p_data;
    +   
    +    if ( newval.f_float < 1.5 )
    +    {
    +        newval.f_float = 1.5;
    +    }
    +    else if ( newval.f_float > 400.0 )
    +    {
    +        newval.f_float = 400.0;
    +    }
    +
    +    vlc_mutex_lock( &p_sys->lock );
    +    p_sys->attack = newval.f_float;
    +    vlc_mutex_unlock( &p_sys->lock );
    +
    +    return VLC_SUCCESS;
    +}
    +
    +static int ReleaseCallback( vlc_object_t *p_this, char const *psz_cmd,
    +                            vlc_value_t oldval, vlc_value_t newval,
    +                            void * p_data )
    +{
    +    VLC_UNUSED(p_this); VLC_UNUSED(psz_cmd); VLC_UNUSED(oldval);
    +    filter_sys_t *p_sys = p_data;
    +   
    +    if ( newval.f_float < 2.0 )
    +    {
    +        newval.f_float = 2.0;
    +    }
    +    else if ( newval.f_float > 800.0 )
    +    {
    +        newval.f_float = 800.0;
    +    }
    +
    +    vlc_mutex_lock( &p_sys->lock );
    +    p_sys->release = newval.f_float;
    +    vlc_mutex_unlock( &p_sys->lock );
    +
    +    return VLC_SUCCESS;
    +}
    +
    +static int ThresholdCallback( vlc_object_t *p_this, char const *psz_cmd,
    +                              vlc_value_t oldval, vlc_value_t newval,
    +                              void * p_data )
    +{
    +    VLC_UNUSED(p_this); VLC_UNUSED(psz_cmd); VLC_UNUSED(oldval);
    +    filter_sys_t *p_sys = p_data;
    +   
    +    if ( newval.f_float < -30.0 )
    +    {
    +        newval.f_float = -30.0;
    +    }
    +    else if ( newval.f_float > 0.0 )
    +    {
    +        newval.f_float = 0.0;
    +    }
    +
    +    vlc_mutex_lock( &p_sys->lock );
    +    p_sys->threshold = newval.f_float;
    +    vlc_mutex_unlock( &p_sys->lock );
    +
    +    return VLC_SUCCESS;
    +}
    +
    +static int RatioCallback( vlc_object_t *p_this, char const *psz_cmd,
    +                          vlc_value_t oldval, vlc_value_t newval,
    +                          void * p_data )
    +{
    +    VLC_UNUSED(p_this); VLC_UNUSED(psz_cmd); VLC_UNUSED(oldval);
    +    filter_sys_t *p_sys = p_data;
    +   
    +    if ( newval.f_float < 1.0 )
    +    {
    +        newval.f_float = 1.0;
    +    }
    +    else if ( newval.f_float > 20.0 )
    +    {
    +        newval.f_float = 20.0;
    +    }
    +
    +    vlc_mutex_lock( &p_sys->lock );
    +    p_sys->ratio = newval.f_float;
    +    vlc_mutex_unlock( &p_sys->lock );
    +
    +    return VLC_SUCCESS;
    +}
    +
    +static int KneeCallback( vlc_object_t *p_this, char const *psz_cmd,
    +                         vlc_value_t oldval, vlc_value_t newval,
    +                         void * p_data )
    +{
    +    VLC_UNUSED(p_this); VLC_UNUSED(psz_cmd); VLC_UNUSED(oldval);
    +    filter_sys_t *p_sys = p_data;
    +   
    +    if ( newval.f_float < 1.0 )
    +    {
    +        newval.f_float = 1.0;
    +    }
    +    else if ( newval.f_float > 10.0 )
    +    {
    +        newval.f_float = 10.0;
    +    }
    +
    +    vlc_mutex_lock( &p_sys->lock );
    +    p_sys->knee = newval.f_float;
    +    vlc_mutex_unlock( &p_sys->lock );
    +
    +    return VLC_SUCCESS;
    +}
    +
    +static int MakeupGainCallback( vlc_object_t *p_this, char const *psz_cmd,
    +                               vlc_value_t oldval, vlc_value_t newval,
    +                               void * p_data )
    +{
    +    VLC_UNUSED(p_this); VLC_UNUSED(psz_cmd); VLC_UNUSED(oldval);
    +    filter_sys_t *p_sys = p_data;
    +   
    +    if ( newval.f_float < 0.0 )
    +    {
    +        newval.f_float = 0.0;
    +    }
    +    else if ( newval.f_float > 24.0 )
    +    {
    +        newval.f_float = 24.0;
    +    }
    +
    +    vlc_mutex_lock( &p_sys->lock );
    +    p_sys->makeup_gain = newval.f_float;
    +    vlc_mutex_unlock( &p_sys->lock );
    +
    +    return VLC_SUCCESS;
    +}
    diff -purN vlc.orig/modules/audio_filter/Modules.am vlc/modules/audio_filter/Modules.am
    --- vlc.orig/modules/audio_filter/Modules.am   2010-06-19 13:09:58.074687899 -0500
    +++ vlc/modules/audio_filter/Modules.am   2010-06-19 13:10:43.144685059 -0500
    @@ -1,5 +1,6 @@
    SUBDIRS = channel_mixer converter resampler spatializer
    SOURCES_equalizer = equalizer.c equalizer_presets.h
    +SOURCES_compressor = compressor.c
    SOURCES_normvol = normvol.c
    SOURCES_audiobargraph_a = audiobargraph_a.c
    SOURCES_param_eq = param_eq.c
    @@ -9,6 +10,7 @@ SOURCES_chorus_flanger = chorus_flanger.
    libvlc_LTLIBRARIES += \
       libaudiobargraph_a_plugin.la \
       libchorus_flanger_plugin.la \
    +   libcompressor_plugin.la \
       libequalizer_plugin.la \
       libnormvol_plugin.la \
       libparam_eq_plugin.la \
    diff -purN vlc.orig/modules/gui/qt4/components/extended_panels.cpp vlc/modules/gui/qt4/components/extended_panels.cpp
    --- vlc.orig/modules/gui/qt4/components/extended_panels.cpp   2010-06-19 13:09:58.144688104 -0500
    +++ vlc/modules/gui/qt4/components/extended_panels.cpp   2010-06-19 13:15:36.317535503 -0500
    @@ -1117,6 +1117,176 @@ void Equalizer::addCallbacks( aout_insta
      **********************************************************************/

    /**********************************************************************
    + * Dynamic range compressor
    + **********************************************************************/
    +static const char *psz_comp_control_names[] =
    +{
    +    "compressor-rms-peak", "compressor-attack", "compressor-release",
    +    "compressor-threshold", "compressor-ratio", "compressor-knee",
    +    "compressor-makeup-gain"
    +};
    +
    +static const char *psz_comp_control_descs[] =
    +{
    +    "RMS/peak", "Attack", "Release", "Threshold", "Ratio", "Knee radius",
    +    "Makeup gain"
    +};
    +
    +static const char *psz_comp_control_units[] =
    +{
    +    "", " ms", " ms", " dB", ":1", " dB", " dB"
    +};
    +
    +static const float f_comp_min_max_val_res_data[][4] =
    +{
    +    //  min    max  value  resolution
    +    // ----  -----  -----  ----------
    +    {   0.0,   1.0,   0.0, 0.001 },  // RMS/peak
    +    {   1.5, 400.0,   1.5, 0.100 },  // Attack
    +    {   2.0, 800.0, 800.0, 0.100 },  // Release
    +    { -30.0,   0.0, -11.0, 0.010 },  // Threshold
    +    {   1.0,  20.0,  10.0, 0.010 },  // Ratio
    +    {   1.0,  10.0,   1.0, 0.010 },  // Knee radius
    +    {   0.0,  24.0,  10.0, 0.010 }   // Makeup gain
    +};
    +
    +Compressor::Compressor( intf_thread_t *_p_intf, QWidget *_parent ) :
    +    QWidget( _parent ) , p_intf( _p_intf )
    +{
    +    QFont smallFont = QApplication::font( static_cast<QWidget*>( 0 ) );
    +    smallFont.setPointSize( smallFont.pointSize() - 3 );
    +
    +    QGridLayout *layout = new QGridLayout( this );
    +    layout->setMargin( 0 );
    +
    +    enableCheck = new QCheckBox( qtr( "Enable dynamic range compressor" ) );
    +    layout->addWidget( enableCheck, 0, 0, 1, NUM_CP_CTRL );
    +
    +    for( int i = 0 ; i < NUM_CP_CTRL ; i++ )
    +    {
    +        compCtrl[i] = new QSlider( Qt::Vertical );
    +
    +        const int i_min = (int)( f_comp_min_max_val_res_data[i][0]
    +                               / f_comp_min_max_val_res_data[i][3] );
    +        const int i_max = (int)( f_comp_min_max_val_res_data[i][1]
    +                               / f_comp_min_max_val_res_data[i][3] );
    +        const int i_val = (int)( f_comp_min_max_val_res_data[i][2]
    +                               / f_comp_min_max_val_res_data[i][3] );
    +
    +        compCtrl[i]->setMinimum( i_min );
    +        compCtrl[i]->setMaximum( i_max );
    +        compCtrl[i]->setValue(   i_val );
    +        oldControlVars[i] = f_comp_min_max_val_res_data[i][2];
    +        CONNECT( compCtrl[i], valueChanged( int ), this, setInitValues() );
    +        ctrl_texts[i] = new QLabel( qtr( psz_comp_control_descs[i] )
    +                                  + qtr( "\n" ) );
    +        ctrl_texts[i]->setFont( smallFont );
    +        ctrl_readout[i] = new QLabel( qtr( "" ) );
    +        ctrl_readout[i]->setFont( smallFont );
    +        layout->addWidget( compCtrl[i], 1, i );
    +        layout->addWidget( ctrl_readout[i], 2, i );
    +        layout->addWidget( ctrl_texts[i], 3, i );
    +    }
    +
    +    BUTTONACT( enableCheck, enable() );
    +
    +    /* Write down initial values */
    +    aout_instance_t *p_aout = THEMIM->getAout();
    +    char *psz_af;
    +
    +    if( p_aout )
    +    {
    +        psz_af = var_GetNonEmptyString( p_aout, "audio-filter" );
    +        for( int i = 0; i < NUM_CP_CTRL; i++ )
    +        {
    +            controlVars[i] = var_GetFloat( p_aout,
    +                                           psz_comp_control_names[i] );
    +        }
    +        vlc_object_release( p_aout );
    +    }
    +    else
    +    {
    +        psz_af = config_GetPsz( p_intf, "audio-filter" );
    +        for( int i = 0; i < NUM_CP_CTRL; i++ )
    +        {
    +            controlVars[i] = config_GetFloat( p_intf,
    +                                              psz_comp_control_names[i] );
    +        }
    +    }
    +    if( psz_af && strstr( psz_af, "compressor" ) != NULL )
    +        enableCheck->setChecked( true );
    +    free( psz_af );
    +    enable( enableCheck->isChecked() );
    +    updateSliders( controlVars );
    +    setValues( controlVars );
    +}
    +
    +Compressor::~Compressor()
    +{
    +}
    +
    +void Compressor::enable()
    +{
    +    bool en = enableCheck->isChecked();
    +    aout_EnableFilter( THEPL, "compressor", en );
    +    enable( en );
    +}
    +
    +void Compressor::enable( bool en )
    +{
    +    for( int i = 0 ; i < NUM_CP_CTRL ; i++ )
    +    {
    +        compCtrl[i]->setEnabled( en );
    +        ctrl_texts[i]->setEnabled( en );
    +        ctrl_readout[i]->setEnabled( en );
    +    }
    +}
    +
    +void Compressor::updateSliders( float * controlVars )
    +{
    +    for( int i = 0 ; i < NUM_CP_CTRL ; i++ )
    +    {
    +        if ( oldControlVars[i] != controlVars[i] )
    +        {
    +            const int i_val = (int)( controlVars[i]
    +                                   / f_comp_min_max_val_res_data[i][3] );
    +            compCtrl[i]->setValue( i_val );
    +        }
    +    }
    +}
    +
    +void Compressor::setInitValues()
    +{
    +    setValues( controlVars );
    +}
    +
    +void Compressor::setValues( float * controlVars )
    +{
    +    aout_instance_t *p_aout = THEMIM->getAout();
    +
    +    for( int i = 0 ; i < NUM_CP_CTRL ; i++ )
    +    {
    +        float f = (float)( compCtrl[i]->value() )
    +                * ( f_comp_min_max_val_res_data[i][3] );
    +        ctrl_readout[i]->setText( QString::number( f, 'f', 1 )
    +                                + qtr( psz_comp_control_units[i] ) );
    +        if( oldControlVars[i] != f )
    +        {
    +            if( p_aout )
    +            {
    +                var_SetFloat( p_aout, psz_comp_control_names[i], f );
    +            }
    +            config_PutFloat( p_intf, psz_comp_control_names[i], f );
    +            oldControlVars[i] = f;
    +        }
    +    }
    +    if( p_aout )
    +    {
    +        vlc_object_release( p_aout );
    +    }
    +}
    +
    +/**********************************************************************
      * Spatializer
      **********************************************************************/
    static const char *psz_control_names[] =
    diff -purN vlc.orig/modules/gui/qt4/components/extended_panels.hpp vlc/modules/gui/qt4/components/extended_panels.hpp
    --- vlc.orig/modules/gui/qt4/components/extended_panels.hpp   2010-06-19 13:09:58.154691544 -0500
    +++ vlc/modules/gui/qt4/components/extended_panels.hpp   2010-06-19 13:13:22.525934483 -0500
    @@ -38,6 +38,7 @@
    #include <QTabWidget>

    #define BANDS 10
    +#define NUM_CP_CTRL 7
    #define NUM_SP_CTRL 5

    class QSignalMapper;
    @@ -115,6 +116,33 @@ private slots:
         void setCorePreset(int);
    };

    +class Compressor: public QWidget
    +{
    +    Q_OBJECT
    +public:
    +    Compressor( intf_thread_t *, QWidget * );
    +    virtual ~Compressor();
    +
    +private:
    +    QSlider *compCtrl[NUM_CP_CTRL];
    +    QLabel *ctrl_texts[NUM_CP_CTRL];
    +    QLabel *ctrl_readout[NUM_CP_CTRL];
    +    float controlVars[7];
    +    float oldControlVars[7];
    +
    +    QCheckBox *enableCheck;
    +
    +    void delCallbacks( aout_instance_t * );
    +    void addCallbacks( aout_instance_t * );
    +    intf_thread_t *p_intf;
    +private slots:
    +    void enable(bool);
    +    void enable();
    +    void updateSliders(float *);
    +    void setValues(float *);
    +    void setInitValues();
    +};
    +
    class Spatializer: public QWidget
    {
         Q_OBJECT
    diff -purN vlc.orig/modules/gui/qt4/dialogs/extended.cpp vlc/modules/gui/qt4/dialogs/extended.cpp
    --- vlc.orig/modules/gui/qt4/dialogs/extended.cpp   2010-06-19 13:09:58.144688104 -0500
    +++ vlc/modules/gui/qt4/dialogs/extended.cpp   2010-06-19 13:12:35.184683318 -0500
    @@ -54,6 +54,9 @@ ExtendedDialog::ExtendedDialog( intf_thr
         equal = new Equalizer( p_intf, audioTab );
         audioTab->addTab( equal, qtr( "Graphic Equalizer" ) );

    +    Compressor *compres = new Compressor( p_intf, audioTab );
    +    audioTab->addTab( compres, qtr( "Compressor" ) );
    +
         Spatializer *spatial = new Spatializer( p_intf, audioTab );
         audioTab->addTab( spatial, qtr( "Spatializer" ) );
         audioLayout->addWidget( audioTab );
```

This patch will supposedly allow me to use dynamic range compression when I watch videos in Ubuntu.  This is VERY important to me.

I have no idea what a "patch" is or what I should do with it.  Any help would be much appreciated!

Thanks!

---

### Post by andrew.46 on 2010-11-11
Hi hurtstotalktoyou,

To apply a patch you would normally need to download the source code, apply the patch and then recompile. Not really advisable with this one though as it was initially applied against the development version of vlc, rather than the release version and looks like [it has already been applied]("http://git.videolan.org/gitweb.cgi?p=vlc.git;a=commit;h=d017a2f8c6ba66405628d5d7adc4978068417924"), in slightly modified form.

Perhaps try building vlc-git, there is a guide for Maverick somewhere on these forums I believe?

Andrew

---

