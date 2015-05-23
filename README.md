# LastFM PHP Album Collage

A Script that takes in `LastFM username` and collages their most played albums in a grid.
Uses S3 to store the images in a persistant manner without filling up the local disk.

---

**Tested using `PHP 5.5` and requires `PHP-GD library` for building the images.**

---

## Requirements

* **AWS IAM Roles** (running on your instance)
* **LastFM API Key**

### IAM Role Sample JSON:

```json
{
  "Statement": [
    {
      "Sid": "Stmt1402566164255",
      "Action": [
        "s3:GetObject",
        "s3:GetObjectVersion",
        "s3:ListBucket",
        "s3:PutObject",
        "s3:PutObjectAcl",
        "s3:PutObjectVersionAcl",
        "s3:DeleteObject"
      ],
      "Effect": "Allow",
      "Resource": [
        "arn:aws:s3:::<Bucket Name/*",
        "arn:aws:s3:::<Bucket Name>"
      ]
    }
  ]
}
```

### Last.FM API Key

Don't forget to fill you API Key in the `config.inc.php` file!

```php
$config['api_key'] = '<LastFM Key>'
```

If no `config.inc.php` file is found, it will use the following environment variables: `api_key` and `bucket`.