=== Form to Post ===
Contributors: msimpson
Donate link: https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=NEVDJ792HKGFN&lc=US&item_name=Wordpress%20Plugin&item_number=cf7%2dto%2ddb%2dextension&currency_code=USD&bn=PP%2dDonationsBF%3abtn_donateCC_LG%2egif%3aNonHosted
Tags:
Requires at least: 3.2.1
Tested up to: 3.2.1
Stable tag: 0.2

Create a WP Post from a Form Submission.

== Description ==

Create a WP Post from a Form Submission. Create a form using Contact Form 7, Fast Secure Contact Form, or just a plain
form, be sure to name your fields correctly, then the form submission will be sent to a post.

Very limited.

* Only accepts text, no images, videos, etc.
* No error handling.

<strong>How To</strong>

1. Create a form using Contact Form 7 (CF7) or Fast Secure Contact Form (FSCF) plugins.
1. Name your fields according to the parameters of the <a href="http://codex.wordpress.org/Function_Reference/wp_insert_post">wp_insert_post function</a>.

Minimally, your form must have the following two fields. A post will not be created if one or both is missing.

* post_title
* post_content

<strong>How to handle categories</strong>
You can create a multiple

If you want to make all the posts be of the same category, create a hidden field. Or you can create
check boxes and allow multiple selection. In either case put in a field named:

* post_category_name

NOTE: if you are familiar with wp_insert_post, then you will know that there is a "post_category" parameter but no
"post_category_name". The problem with "post_category" is it requires category ids (the numbers). But what you really
want in a form are the category names. So this plug allows for "post_category_name" which can be one or more
category names. It looks up the associated category numbers and sets "post_category" for wp_insert_post.

CF7 Form Definition Example:

<pre><code>
Post Title [text* post_title] &lt;br/&gt;

Post Content (required) &lt;br/&gt;
   [textarea* post_content] &lt;br/&gt;

Categories (required) &lt;br/&gt;
  [checkbox* post_category_name "Uncategorized" "Cat1" "Cat2" "Cat3"] &lt;br/&gt;

[submit "Post"] &lt;br/&gt;

</code></pre>

<strong>Not using CF7 nor FSCF</strong>
You can define your own form naming fields as described above. But you need to do one extra step in this case.
You need to have the target page of your form insert the data in the post. You do this by means of a short code [capture-form-to-post].
Simply place the short code on your form's target page and it will capture the submission and create a post.

Plain Form Example:

In this example, we create our own form, that posts to the same page. So we put both the short code and the form
definition in the same page. The short code only does something when there are post parameters.
NOTE: your form must have method="post" not "get".

<pre><code>
[capture-form-to-post]
&lt;form action="" method="post"&gt;
   Post Title: &lt;input type="text" name="post_title" value=""/&gt;&lt;br/&gt;
   Post Content: &lt;br/&gt;
   &lt;textarea rows="10" name="post_content" cols="20"&gt;&lt;/textarea&gt;
   &lt;input type="checkbox" name="post_category_name[]" value="Uncategorized"&gt;Uncategorized&lt;br&gt;
   &lt;input type="checkbox" name="post_category_name[]" value="Cat1"&gt;Cat1&lt;br&gt;
   &lt;input type="checkbox" name="post_category_name[]" value="Cat2"&gt;Cat2&lt;br&gt;
   &lt;input type="checkbox" name="post_category_name[]" value="Cat3"&gt;Cat3&lt;br&gt;
   &lt;input type="submit" /&gt;
&lt;/form&gt;
</code></pre>

Remember: do NOT use [capture-form-to-post] if your form is a CF7 or FSCF form.

Advanced:

There are many more parameters to wp_insert_post that can be set simply by putting a form fields in your form
of the same name as the wp_insert_post parameter. Examples are:

* post_status which will be set to 'publish' by default making the post published automatically. But you could set that in a hidden field to 'draft', 'publish', 'pending', 'future', 'private'
* comment_status which can be 'closed' or 'open'
* post_excerpt
* post_date (format: <a href="http://php.net/manual/en/function.date.php">Y-m-d H:i:s</a>, e.g. "2012-01-01 15:30:00")
* And many more, see <a href="http://codex.wordpress.org/Function_Reference/wp_insert_post">wp_insert_post function</a>
* NOTE: tax_input is NOT supported.
* NOTE: If you would want to edit a form, you would need to get the post's ID and put it in a form 'ID' field.

== Installation ==


== Frequently Asked Questions ==


== Screenshots ==


== Changelog ==

= 0.2 =

Fixed issue related to date.

= 0.1 =

Initial Revision
