<template>
    <div class="content">
        <p class="title">
            {{ $t('common.error403.title') }}
        </p>
        <div class="description text-center mb-10 mt-10">
            {{ $t('common.error403.description') }}
        </div>
        <div class="button">
            <common-primary-button
                :text="$t('common.error403.button')"
                @click.native="goToHomePage"
            />
        </div>
    </div>
</template>

<script>
import TokenService from '@/helpers/token';
import { HOME_PAGE_NAME } from '@/helpers/constants';

export default {
    methods: {
        goToHomePage() {
            const isLogin = !!TokenService.getToken();
            if (isLogin) {
                this.$router.push({ name: HOME_PAGE_NAME }).catch(() => {});
            } else {
                this.$router.push({ name: 'LoginPage' }).catch(() => {});
            }
        },
    },
};
</script>

<style lang="scss" scoped>
.content {
    .title {
    }
    .button {
        text-align: center;
    }
    .description {
        max-width: 42rem;
        margin: auto;
    }
    align-items: center;
    margin: auto;
    padding: 4rem 1rem;
    text-align: center;
}
</style>
