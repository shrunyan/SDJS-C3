<template lang="pug">
.section.newsletter-section
  .nav-target#subscribe
  .container__inner
    label.form__label
      | Vue.js Newsletter
    .newsletter-section__input-wrapper(id="revue-embed")
      form(action="https://www.getrevue.co/profile/vuenewsletter/add_subscriber" method="post" id="revue-form" name="revue-form"  target="_blank")
        input.form__input(placeholder="Your email address..." type="email" name="member[email]" id="member_email" autocomplete="off" required)
        input.button.button--dark(
          type="submit",
          value="Subscribe",
          name="member[subscribe]",
          id="member_submit",
          @click="trackNewsletterEvent"
        )

    p.newsletter__paragraph
      | Subscribe to the Vue.js Newsletter to receive weekly updates on everything Vue-related! Conference included.
</template>

<script>
export default {
  methods: {
    trackNewsletterEvent (event) {
      ga('send', 'event', {
        eventAction: 'click',
        eventCategory: 'Newsletter sub',
        transport: 'beacon'
      })
    }
  }
}
</script>

<style lang="sass" scoped>
  @import ~assets/css/base/helpers

  .newsletter__paragraph
    line-height: 1.4
    font:
      size: 20px
      weight: 300
    margin-bottom: 0

    @media #{$medium-up}
      font-size: 24px

  .newsletter-section__input-wrapper
    position: relative
    display: inline-block
    width: 100%
    vertical-align: middle
    text-align: center

    @media #{$medium-up}
      text-align: left
      margin-left: 50px
      width: 55%

      .button
        position: absolute
        top: 5px
        right: 5px

    @media #{$small-only}
      .button
        margin-top: 20px
</style>
