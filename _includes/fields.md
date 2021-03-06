{% capture brooklyn_version %}0.7.0-SNAPSHOT{% endcapture %}

{% if brooklyn_version contains 'SNAPSHOT' %}{% capture SNAPSHOT %}true{% endcapture %}{% endif %}

{% capture brooklyn_examples_branch %}{% if SNAPSHOT %}{{ site.brooklyn-snapshot-git-branch }}{% else %}{{ brooklyn_version }}{% endif %}{% endcapture %}

{% capture cloudsoft_snapshots_base_url %}http://developers.cloudsoftcorp.com/maven/snapshots/{% endcapture %}
{% capture cloudsoft_releases_base_url %}http://developers.cloudsoftcorp.com/maven/releases/{% endcapture %}
{% capture cloudsoft_this_version_base_url %}http://developers.cloudsoftcorp.com/maven/{% if SNAPSHOT %}snapshots/{% else %}releases/{% endif %}{% endcapture %}

{% capture cloudsoft_this_version_groupid_url %}{{ cloudsoft_this_version_base_url }}io/brooklyn/{% endcapture %}
{% capture cloudsoft_this_dist_url_dir %}{{ cloudsoft_this_version_groupid_url }}brooklyn-dist/{{ brooklyn_version }}/{% endcapture %}
{% capture cloudsoft_this_alljar_url_dir %}{{ cloudsoft_this_version_groupid_url }}brooklyn-all/{{ brooklyn_version }}/{% endcapture %}

<!--- both snapshots and releases -->
{% capture sonatype_repo_groupid_url %}https://oss.sonatype.org/content/groups/public/io/brooklyn/{% endcapture %}
<!--- releases --> 
{% capture mavencentral_repo_groupid_url %}http://repo1.maven.org/maven2/io/brooklyn/{% endcapture %}

{% if SNAPSHOT %}
  {% capture this_anything_url_search %}https://oss.sonatype.org/index.html#nexus-search;gav~io.brooklyn~~{{ brooklyn_version }}~~{% endcapture %}
  {% capture this_dist_url_search %}https://oss.sonatype.org/index.html#nexus-search;gav~io.brooklyn~brooklyn-dist~{{ brooklyn_version }}~~{% endcapture %}
  {% capture this_alljar_url_search %}https://oss.sonatype.org/index.html#nexus-search;gav~io.brooklyn~brooklyn-dist~{{ brooklyn_version }}~~{% endcapture %}
  {% capture this_dist_url_dir %}{{ sonatype_repo_groupid_url }}brooklyn-dist/{{ brooklyn_version }}/{% endcapture %}
  {% capture this_alljar_url_dir %}{{ sonatype_repo_groupid_url }}brooklyn-all/{{ brooklyn_version }}/{% endcapture %}
  {% capture this_dist_url_zip %}https://oss.sonatype.org/service/local/artifact/maven/redirect?r=snapshots&g=io.brooklyn&v={{ brooklyn_version }}&a=brooklyn-dist&c=dist&e=zip{% endcapture %}
  {% capture this_dist_url_tgz %}https://oss.sonatype.org/service/local/artifact/maven/redirect?r=snapshots&g=io.brooklyn&v={{ brooklyn_version }}&a=brooklyn-dist&c=dist&e=tar.gz{% endcapture %}
  {% capture this_alljar_url_jar  %}https://oss.sonatype.org/service/local/artifact/maven/redirect?r=snapshots&g=io.brooklyn&v={{ brooklyn_version }}&a=brooklyn-all&c=with-dependencies&e=jar{% endcapture %}
{% else %}<!--- RELEASE -->
  {% capture this_anything_url_search %}http://search.maven.org/#search%7Cgav%7C1%7Cg%3A%22io.brooklyn%22%20AND%20v%3A%22{{ brooklyn_version }}%22{% endcapture %}
  {% capture this_dist_url_search %}http://search.maven.org/#search%7Cgav%7C1%7Cg%3A%22io.brooklyn%22%20AND%20a%3A%22brooklyn-dist%22%20AND%20v%3A%22{{ brooklyn_version }}%22{% endcapture %}
  {% capture this_alljar_url_search %}http://search.maven.org/#search%7Cgav%7C1%7Cg%3A%22io.brooklyn%22%20AND%20a%3A%22brooklyn-all%22%20AND%20v%3A%22{{ brooklyn_version }}%22{% endcapture %}
  {% capture this_dist_url_dir %}{{ mavencentral_repo_groupid_url }}brooklyn-dist/{{ brooklyn_version }}/{% endcapture %}
  {% capture this_alljar_url_dir %}{{ mavencentral_repo_groupid_url }}brooklyn-all/{{ brooklyn_version }}/{% endcapture %}
  {% capture this_dist_url_zip %}{{ mavencentral_repo_groupid_url }}brooklyn-dist/{{ brooklyn_version }}/brooklyn-dist-{{ brooklyn_version }}-dist.zip{% endcapture %}
  {% capture this_dist_url_tgz %}{{ mavencentral_repo_groupid_url }}brooklyn-dist/{{ brooklyn_version }}/brooklyn-dist-{{ brooklyn_version }}-dist.tar.gz{% endcapture %}
  {% capture this_alljar_url_jar %}{{ mavencentral_repo_groupid_url }}brooklyn-all/{{ brooklyn_version }}/brooklyn-all-{{ brooklyn_version }}-with-dependencies.jar{% endcapture %}
{% endif %}
